```
remove_weight_norms(x)
```

Remove any [WeightNorm](@ref) parametrization in the model.

### Example

```jldoctest
julia> model = Chain(
           WeightNorm(Conv((3,), 1 => 2), :weight),
           WeightNorm(Conv((3,), 2 => 2), :weight),
       )
Chain(
  WeightNorm(
    Conv((3,), 1 => 2),                 # 8 parameters
    3×1×1 Array{Float32,...},           # 3 parameters
    :weight,
    3,
  ),
  WeightNorm(
    Conv((3,), 2 => 2),                 # 14 parameters
    3×2×1 Array{Float32,...},           # 6 parameters
    :weight,
    3,
  ),
)                   # Total: 6 arrays, 31 parameters, 588 bytes.

julia> Flux.remove_weight_norms(model)
Chain(
  Conv((3,), 1 => 2),                   # 8 parameters
  Conv((3,), 2 => 2),                   # 14 parameters
)                   # Total: 4 arrays, 22 parameters, 392 bytes.
```
