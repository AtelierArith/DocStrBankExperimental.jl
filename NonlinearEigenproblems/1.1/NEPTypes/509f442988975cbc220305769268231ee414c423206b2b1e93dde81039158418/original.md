```
function estimate_error(E::ErrmeasureType,λ,v)
```

Returns the error estimate for the eigenpair `(λ,v)`. The way to measure the error is specified in `E`, which can be an `Errmeasure` or a `Function`.

See also: [`Errmeasure`](@ref), [`ErrmeasureType`](@ref)
