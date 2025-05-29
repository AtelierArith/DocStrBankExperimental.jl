```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}, N::Integer; λmin::Real=-Inf, λmax::Real=Inf)
```

Fit the dielectric constant data `ε` sampled at wavelengths `λ` to the Sellmeier equation with exactly `N` terms.  Only the entries of `λ` between `λmin` and `λmax` and the corresponding entries of `ε` are used.  Among the `N` terms, some are below and the other are above the range of `λ`.
