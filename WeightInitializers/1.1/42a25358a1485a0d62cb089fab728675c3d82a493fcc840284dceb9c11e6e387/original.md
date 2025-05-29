```
randnC64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF64, length(size)}
```

Return an `AbstractArray{ComplexF64}` of the given `size` containing random numbers from a standard normal distribution.
