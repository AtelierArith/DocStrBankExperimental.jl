```
jacobian_transpose_v(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

Returns a vector of Node, where each element in the vector is the symbolic form of `Jᵀv`. Also returns `v_vector` a vector of the `v` variables. This is useful if you want to generate a function to evaluate `Jᵀv` and you want to separate the inputs to the function and the `v` variables.
