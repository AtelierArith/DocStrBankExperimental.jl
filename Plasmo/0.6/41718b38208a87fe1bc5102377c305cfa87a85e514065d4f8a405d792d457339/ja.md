```
neighborhood(
    hyper::HyperGraphProjection, 
    nodes::Vector{OptiNode}, 
    distance::Int64
)::Vector{OptiNode}
```

与えられた `nodes` の `optigraph` `graph` 内の `distance` 以内の optinodes を返します。
