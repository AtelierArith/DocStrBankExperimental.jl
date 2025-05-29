```
ParallelExhaustiveSearch(; dist=SqL2Distance(), db=VectorDatabase{Float32}())
```

クエリを解決し、データセット内のクエリとすべての要素に対して `dist` を並列で評価します。これは `searchbatch(...; parallel=true)` と併用しないでください。リソースを競合することになります。
