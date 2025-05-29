```
tensor(v::Array{T,2}; dtype=Float64, sparse=false) where T
```

Convert a generic array `v` to a tensor. For example, 

```julia
v = [0.0 constant(1.0) 2.0
    constant(2.0) 0.0 1.0]
u = tensor(v)
```

`u` will be a $2\times 3$ tensor. 

!!! note
    This function is expensive. Use with caution.

