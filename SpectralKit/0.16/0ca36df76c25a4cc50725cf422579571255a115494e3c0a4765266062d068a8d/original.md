```julia
linear_combination(basis, θ)

```

Return a callable that calculates `linear_combination(basis, θ, x)` when called with `x`.

You can use `linear_combination(basis, θ) ∘ transformation` for domain transformations, though working with `basis ∘ transformation` may be preferred.
