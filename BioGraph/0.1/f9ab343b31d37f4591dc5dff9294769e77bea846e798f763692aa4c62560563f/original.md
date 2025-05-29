```
find_longest_path(graph_result::BioGraph.GraphResult, optimizer_factory; is_weighted::Bool, source_node::Int64, sink_node::Int64, has_path::String)
```

Find longest path in graph. Input:

  * `GraphResult`
  * JuMP optimizer_factory such as `CPLEX.Optimizer`
  * `has_path`: optional string that indicates the path must have in longest path.
  * `is_weighted`: if `true` find shortest path which is weighted
  * `source_node`, `sink_node`: find longest path which has source and sink nodes.
