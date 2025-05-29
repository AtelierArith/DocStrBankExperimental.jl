```
loadgraph(file, gname="graph", format=LGFormat())
```

Read a graph named `gname` from `file` in the format `format`.

### Implementation Notes

`gname` is graph-format dependent and is only used if the file contains multiple graphs; if the file format does not support multiple graphs, this value is ignored. The default value may change in the future.
