```
MetaGraph(::Client, resource::MBQCResourceState)
```

This function creates a MetaGraph from a given MBQCResourceState. It extracts the graph from the resource state and wraps it in a MetaGraph.

# Arguments

  * `client::Client`: The client object.
  * `resource::MBQCResourceState`: The MBQC resource state containing the graph.

# Examples

`julia client = Client() resource = MBQCResourceState(graph) MetaGraph(client, resource)``
