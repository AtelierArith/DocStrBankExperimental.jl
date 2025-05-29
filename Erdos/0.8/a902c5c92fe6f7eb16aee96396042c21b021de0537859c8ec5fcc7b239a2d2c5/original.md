```
writenetwork(file, g)
writenetwork(file, g, t; compress=false)
```

Save a network `g` to `file` in the format `t`.

Eventually the resulting file can be compressed in the gzip format.

Currently supported formats are `:gml, :graphml, :gexf, :dot, :net, :gt`. When possible, graph, edge, and vertex properties will be written as well.

If no format is provided, it will be inferred from `file` along with compression.
