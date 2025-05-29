```
rand16([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float16, length(size)}
```

Return an `AbstractArray{Float16}` of the given `size` containing random numbers from a uniform distribution.
