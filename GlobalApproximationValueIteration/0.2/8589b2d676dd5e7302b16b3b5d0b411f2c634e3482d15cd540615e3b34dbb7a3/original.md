```
compute_value(gfa::GlobalFunctionApproximator, v::AbstractVector)
```

Return the value of the function at some query point v, based on the global function approximator

```
compute_value(gfa::GlobalFunctionApproximator, v_list::AbstractVector{V}) where V <: AbstractVector{Float64}
```

Return the value of the function for a list of query points, based on the global function approximator
