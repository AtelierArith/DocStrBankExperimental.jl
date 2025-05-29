```
Context
```

Data structure than links a node to the rest of the graph.

## Fields

  * `graph`: Dynamic graph that contains the node.
  * `node`: Node inside the graph.

## Details

A `Context` object wraps references to a node and its associated graph. The purpose of this structure is to be able to test relationships among nodes within a graph (from with a query or rule), as well as access the data stored in a node (with `data()`) or the graph (with `graph_data()`).

Users do not build `Context` objects directly but they are provided by VPL as inputs to the user-defined functions inside rules and queries.
