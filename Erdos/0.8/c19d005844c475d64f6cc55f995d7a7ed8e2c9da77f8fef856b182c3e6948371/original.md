```
readgraph(filename, G=Graph)
readgraph(filename, t, G=Graph; compressed=false)
```

Reads a graph from  `filename` in the format `t`. Returns a graph of type `G` or the corresponding digraph/graph type. Compressed files can eventually be read.

Supported formats are `:gml, :dot, :graphml, :gexf, :net, :gt`.

If no format is provided, it will be inferred from `filename`.

```
readgraph(s::Symbol, G=Graph)
```

Read a graph identified by `s` from Erdos datasets collection (e.g. `s=:karate`). They are stored in the `gt` binary format in the `datasets` directory of the package. For a list of available graph refer to the documentation.
