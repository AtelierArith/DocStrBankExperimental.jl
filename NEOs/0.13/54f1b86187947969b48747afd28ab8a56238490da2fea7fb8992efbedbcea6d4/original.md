```
jplcompare(des::String, sol::NEOSolution{T, U}) where {T <: Real, U <: Number}
```

Return `abs.(sol() - R) ./ sigmas(sol)`, where `R` is JPL's state vector of object `des` at `sol`'s  initial epoch.
