```
neighborhood(
    hyper::HyperGraphProjection, 
    nodes::Vector{OptiNode}, 
    distance::Int64
)::Vector{OptiNode}
```

Return the optinodes within `distance` of the given `nodes` in the optigraph `graph`.
