```
export_cgd(file, pge::PeriodicGraphEmbedding, name=basename(splitext(file)[1]), append=false)
export_cgd(file, g::PeriodicGraph, name=basename(splitext(file)[1]), append=false)
```

Export a `PeriodicGraph` or a `PeriodicGraphEmbedding` to a .cgd `file` (readable by Systre).

If `append` is set, the graph is added at the end of the file.
