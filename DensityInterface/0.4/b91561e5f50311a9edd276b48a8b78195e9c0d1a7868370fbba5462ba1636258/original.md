```
logdensityof(object)
```

Return a function that computes the logarithmic value of the density `object` (resp. its associated density) at a given point.

```jldoctest a
julia> log_f = logdensityof(object); log_f isa Function
true

julia> log_f(x) == logdensityof(object, x)
true
```

`logdensityof(object)` defaults to `Base.Fix1(logdensityof, object)`, but may be specialized. If so, [`logfuncdensity`](@ref) will typically have to be specialized for the return type of `logdensityof` as well.

[`logfuncdensity`](@ref) is the inverse of `logdensityof`, so `logfuncdensity(log_f)` must be equivalent to `object`.
