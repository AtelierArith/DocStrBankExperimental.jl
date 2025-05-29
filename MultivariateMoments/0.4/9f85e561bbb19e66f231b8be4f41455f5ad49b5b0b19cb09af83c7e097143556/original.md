```
doubt(σ, check::RankCheck)
```

Returns a value measuring the doubt of the rank check `check`. Lower values means more doubt so less certainty. This is used by [`FallbackRank`](@ref) for deciding whether the fallback should be used.
