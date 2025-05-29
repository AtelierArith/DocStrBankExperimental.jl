```
compute_value(lfa::LocalFunctionApproximator, v::AbstractVector)
```

Return the value of the function at some query point v, based on the local function approximator

```
compute_value(lfa::LocalFunctionApproximator, v_list::AbstractVector{V}) where V <: AbstractVector{Float64}
```

Return the value of the function for a list of query points, based on the local function approximator
