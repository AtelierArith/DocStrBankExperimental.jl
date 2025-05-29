```
StabilityReport()
StabilityReport(unstable_variables::Vector{Tuple{Symbol, Type}})
```

Holds information about the stability of a method.

If `unstable_vars` is present, set the fields.  Otherwise, creates an empty set.

See [`is_stable`](@ref)
