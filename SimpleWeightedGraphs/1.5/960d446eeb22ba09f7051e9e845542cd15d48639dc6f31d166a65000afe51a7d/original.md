```
SWGFormat
```

The storage format of SimpleWeightedGraph files. Multiple graphs may be present in one file.

For each graph, the file contains a one line header:

```
"LightGraphs.SimpleWeightedGraph", <num_vertices>, <num_edges>, {"d" | "u"}, <name>[, <ver>, <vdatatype>, <wdatatype>, <graphcode>]
```

  * `"LightGraphs.SimpleWeightedGraph"` is a fixed string
  * `<num_vertices>` is an integer
  * `<num_edges>` is an integer
  * `"d"` for directed graph, `"u"` for undirected (note that this   option does not perform any additional edge construction, it's   merely used to return the correct type of graph)
  * `<name>` is a string
  * `<ver>` is an int
  * `<vdatatype>` is a string ("UInt8", etc.)
  * `<wdatatype>` is a string describing the data type of the weights
  * `<graphcode>` is a string.

The header is followed by a list of (comma-delimited) edges, each on a separate line:

```
<src>,<dst>,<weight>
```

  * `<src>` is an int giving the source of the edge
  * `<dst>` is an int giving the destination of the edge
  * `<weight>` is a real giving the weight of the edge
