```
log∂log(Z::Rotor)
```

Return the value and gradient of `log(Z)` with respect to the components of `Z`.

See [`∂log`](@ref) for more explanation of the components of the gradient.

# Examples

```julia
julia> l, ∂l = log∂log(randn(RotorF64));

```
