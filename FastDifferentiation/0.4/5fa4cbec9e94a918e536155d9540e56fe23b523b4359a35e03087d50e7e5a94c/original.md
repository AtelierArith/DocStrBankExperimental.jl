```
sparse_jacobian(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

Returns a sparse array containing the Jacobian of the function defined by `terms`
