```
LinkedJobList()
LinkedJobList(j::Job)
```

すべてのジョブは ONE `LinkedJobList` のみ存在できます。`LinkedJobList` のすべての反復コピーは `Vector{Job}` を出力します。
