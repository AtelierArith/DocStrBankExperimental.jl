```
parameter_observed(indp, sym)
```

Return the observed function of `sym` in `indp`. This functions similarly to [`observed`](@ref) except that `u` is not an argument of the returned function. For time- dependent systems, the returned function must have the signature `(p, t) -> [values...]`. For time-independent systems, the returned function must have the signature `(p) -> [values...]`.

By default, this function returns `nothing`, indicating that the index provider does not support generating parameter observed functions.
