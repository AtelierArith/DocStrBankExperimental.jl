```julia
mix(α, ℓ1, ℓ2)

```

A *mixture* of two densities: `ℓ1(x)` with probability `α(x)`, and `ℓ2(x)` with probability `1-α(x)`. `α` needs to implement [`weight_and_gradient`](@ref).
