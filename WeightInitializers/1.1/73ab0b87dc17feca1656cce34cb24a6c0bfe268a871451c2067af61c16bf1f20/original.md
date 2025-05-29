```
randn64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float64, length(size)}
```

Return an `AbstractArray{Float64}` of the given `size` containing random numbers from a standard normal distribution.
