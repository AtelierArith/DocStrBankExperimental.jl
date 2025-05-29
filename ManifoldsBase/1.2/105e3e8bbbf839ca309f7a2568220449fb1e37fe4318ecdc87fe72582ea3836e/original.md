```
CompositeManifoldError{T} <: Exception
```

A composite type to collect a set of errors that occured. Mainly used in conjunction with [`ComponentManifoldError`](@ref) to store a set of errors that occured.

# Fields

  * `errors` a `Vector` of `<:Exceptions`.
