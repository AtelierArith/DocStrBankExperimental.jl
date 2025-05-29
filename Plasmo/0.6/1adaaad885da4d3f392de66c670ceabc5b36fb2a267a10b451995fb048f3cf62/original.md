```
aggregate_to_depth!(graph::OptiGraph, max_depth::Int64=0)
```

Aggregate `graph` by converting subgraphs into optinodes. The `max_depth` determines how many levels of subgraphs remain in the new aggregated optigraph. For example, a `max_depth` of `0` signifies there should be no subgraphs in the aggregated optigraph. This version of the method modifies the optigraph and transforms it  into the aggregated version. 
