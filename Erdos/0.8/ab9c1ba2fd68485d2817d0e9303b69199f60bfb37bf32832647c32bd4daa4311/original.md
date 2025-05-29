```
readnetwork(filename, G=Network)
readnetwork(filename, t, G=Network; compressed=false)
```

Read a network from  `filename` in the format `t`.  Returns a network of type `G` (or the corresponding directed/undirected type if needed). Compressed files can eventually be read.

Supported formats are `:gml, :dot, :graphml, :gexf, :net, :gt`. When possible, graph, edge, and vertex properties will be read as well.

If no format is provided, it will be inferred from the `filename`.

```
readnetwork(s::Symbol, G=Network)
```

Read a network identified by `s` from Erdos' datasets collection (e.g. `s=:karate`). They are stored in the `gt` binary format in the `datasets` directory of the package. For a list of available graph refer to the documentation.
