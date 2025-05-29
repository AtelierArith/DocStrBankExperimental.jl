```
exp∂exp(Z::QuatVec)
```

Return the value and gradient of `exp(Z)` with respect to the components of `Z`.

See [`∂exp`](@ref) for more explanation of the components of the gradient.

# Examples

```julia
julia> e, ∂e = exp∂exp(randn(QuatVecF64));

```
