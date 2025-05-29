```
write_nexus(fname::String,tree::FelNode)
```

Writes the tree as a nexus file, suitable for opening in eg. FigTree. Data in the `node_data` dictionary will be converted into annotations. Only tested for simple `node_data` formats and types.
