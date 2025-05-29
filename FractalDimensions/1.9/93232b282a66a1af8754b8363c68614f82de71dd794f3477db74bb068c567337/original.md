```
boxassisted_correlation_dim(X::AbstractStateSpaceSet; kwargs...)
```

Use the box-assisted optimizations of [BuenoOrovio2007](@cite) to estimate the correlation dimension `Δ_C` of `X`.

This function does something extremely simple:

```julia
εs, Cs = boxed_correlationsum(X; kwargs...)
slopefit(log2.(εs), log2.(Cs))[1]
```

and hence see [`boxed_correlationsum`](@ref) for more information and available keywords.
