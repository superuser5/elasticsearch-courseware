# Multi-Index Operations and Aliases #

* ElasticSearch is not a traditional database, searches can be executed acorss indices with no known performance implications
* Entire cluster search:
```
curl 'localhost:9200/_search?q=id:1'
```
* Multiple indices search:
```
curl 'localhost:9200/index1,index2/_search?q=id:1'
```
* Wildcard search:
```
curl 'localhost:9200/index*/_search?q=id:*'
```
* Index alias - create an alias for index or for group of indexes:
```
curl -XPOST 'http://localhost:9200/_aliases' -H 'content-type: application/json' -d '
{
    "actions" : [
        { "add" : { "index" : "test1", "alias" : "alias1" } },
        { "add" : { "index" : "test2", "alias" : "alias1" } }
    ]
}'
```
* Why bother creating aliases? Logical data partitioning, archiving by index, access control...
