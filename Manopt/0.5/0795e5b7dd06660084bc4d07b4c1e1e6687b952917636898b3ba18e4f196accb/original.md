```
RecordEntry{T} <: RecordAction
```

record a certain fields entry of type {T} during the iterates

# Fields

  * `recorded_values` : the recorded Iterates
  * `field`           : Symbol the entry can be accessed with within [`AbstractManoptSolverState`](@ref)

# Constructor

```
RecordEntry(::T, f::Symbol)
RecordEntry(T::DataType, f::Symbol)
```

Initialize the record action to record the state field `f`, and initialize the `recorded_values` to be a vector of element type `T`.

# Examples

  * `RecordEntry(rand(M), :q)` to record the points from `M` stored in some states `s.q`
  * `RecordEntry(SVDMPoint, :p)` to record the field `s.p` which takes values of type [`SVDMPoint`](@extref `Manifolds.SVDMPoint`).
