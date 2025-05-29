```
corner_frequency(m::U, src::SourceParameters{S,T}) where {S<:Float64, T<:Real, U<:Real}
```

Computes a 3-tuple of corner frequency components, depending upon source spectrum type. By default the single-corner Brune spectrum is considered, but if `src.model` equals `:Atkinson_Silva_2000` then the components of the double-corner spectrum are returned. If some other symbol is passed then the Brune model is returned.

# Examples

```julia-repl
    m = 6.0
    Δσ = 100.0
    κ0 = 0.035
    fas = FASParams(Δσ, κ0)
    # compute single corner frequency
	src.model = :Brune
    fc, tmp1, tmp2 = corner_frequency(m, src)
    # compute double corner frequencies
	src.model = :Atkinson_Silva_2000
    fa, fb, ε = corner_frequency(m, src)
```
