```
writegraph(file, g)
writegraph(file, g, t; compress=false)
```

Save a graph `g` to `file` in the format `t`.

Eventually the resulting file can be compressed in the gzip format.

Currently supported formats are `:gml, :graphml, :gexf, :dot, :net, :gt`.

If no format is provided, it will be inferred from `file` along with compression.
