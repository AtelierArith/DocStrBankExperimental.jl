```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}; λmin::Real=-Inf, λmax::Real=Inf, Nmax::Integer=10, rtol_λres::Real=1e-3)
```

Fit the dielectric constant data `ε` sampled at wavelengths `λ` to the Sellmeier equation with up to `Nmax` terms.  Only the entries of `λ` between `λmin` and `λmax` and the corresponding entries of `ε` are used.  If `λres` of different terms have relative difference less than`rtol_λres`, they are considered the same term and merged.
