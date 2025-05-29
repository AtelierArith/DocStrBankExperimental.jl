```
AbstractStatsProcedure{Alias, T<:NTuple{N,StatsStep} where N}
```

Supertype for all types specifying the procedure for statistical estimation or inference.

Fallback methods for indexing and iteration are defined for all subtypes of `AbstractStatsProcedure`.

# Parameters

  * `Alias::Symbol`: alias of the type for pretty-printing.
  * `T<:NTuple{N,StatsStep}`: steps involved in the procedure.
