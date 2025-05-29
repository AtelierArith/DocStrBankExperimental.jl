```
LowfreqPowerSpectrum(; q_lofreq = 0.1)
```

Return a [`PrecomputableFunction`](@ref) containing all the necessary fields to generate a [`PrecomputedLowfreqPowerSpectrum`](@ref). The latter can be initialized by [`precompute`](@ref):

```julia
lfps = precompute( LowfreqPowerSpectrum() )
```

Keyword arguments:

  * `q_lofreq`: a number between `0` and `1` that characterises which portion of the

frequency spectrum is considered to be low. For instance, `q_lofreq = 0.1` implies  that the lowest 10% of frequencies are considered to be the low ones.
