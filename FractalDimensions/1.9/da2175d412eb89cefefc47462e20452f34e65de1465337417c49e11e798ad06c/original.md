```
grassberger_proccacia_dim(X::AbstractStateSpaceSet, εs = estimate_boxsizes(data); kwargs...)
```

Use the method of Grassberger and Proccacia [Grassberger1983](@cite), and the correction by [Theiler1986](@cite), to estimate the correlation dimension `Δ_C` of  `X`.

This function does something extremely simple:

```julia
cm = correlationsum(data, εs; kwargs...)
Δ_C = slopefit(rs, ys)(log2.(sizes), log2.(cm))[1]
```

i.e. it calculates [`correlationsum`](@ref) for various radii and then tries to find a linear region in the plot of the log of the correlation sum versus log(ε).

See [`correlationsum`](@ref) for the available keywords. See also [`takens_best_estimate_dim`](@ref), [`boxassisted_correlation_dim`](@ref).
