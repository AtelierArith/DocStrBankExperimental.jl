```
randC32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF32, length(size)}
```

Return an `AbstractArray{ComplexF32}` of the given `size` containing random numbers from a uniform distribution.
