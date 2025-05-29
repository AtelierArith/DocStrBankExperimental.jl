```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}, Nₙ::Integer, Nₚ::Integer; λmin::Real=-Inf, λmax::Real=Inf)
```

Fit the dielectric constant data `ε` sampled at wavelengths `λ` to the Sellmeier equation with exactly `Nₙ` terms below and `Nₚ` terms above the range of `λ`.  Only the entries of `λ` between `λmin` and `λmax` and the corresponding entries of `ε` are used.
