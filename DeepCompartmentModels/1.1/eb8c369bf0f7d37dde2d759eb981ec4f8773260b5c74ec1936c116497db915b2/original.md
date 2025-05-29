```
make_branch(covariate_idx, layers...)
```

Internal function used to create branches. Allows one to create more specific branch layers. Appends the `layers` to the following Lux.Chain:

```julia
Chain(
    SelectDim(1, covariate_idx),
    ReshapeLayer((1,)),
    layers...
)
```

# Arguments:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: Index of the covariate(s) to use in the branch.
  * `layers`: Layers used to build the neural network.
