```
using_spinedb(url::String, mod=@__MODULE__; upgrade=false, filters=Dict(), extend=false)
```

Extend module `mod` with convenience functions to access the contents of a Spine DB. The argument `url` is either the url of the DB, or of an HTTP Spine DB server associated with it.

# Keyword arguments

  * `upgrade`: if `true`, then the database is upgraded to the latest revision.
  * `filters`: a `Dict` specifying filters.
  * `extend`: if `false`, then any convenience functions already created in the given module are overwritten. Otherwise they are extended.

See [`ObjectClass()`](@ref), [`RelationshipClass()`](@ref), and [`Parameter()`](@ref) for details on how to call the convenience functors.
