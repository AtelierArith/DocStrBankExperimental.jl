```
abstract type Snapshots{T,N,D,I<:AbstractDofMap{D},R<:AbstractRealization,A}
  <: AbstractSnapshots{T,N} end
```

Type representing a collection of parametric abstract arrays of eltype `T`, that are associated with a realization of type `R`. The (spatial) entries of any instance of `Snapshots` are indexed according to an index map of type `I`:AbstractDofMap{`D`}, where `D` encodes the spatial dimension. Note that, as opposed to subtypes of `AbstractParamArray`, which are arrays of arrays, subtypes of `Snapshots` are arrays of numbers.

Subtypes:

  * [`SteadySnapshots`](@ref)
  * [`TransientSnapshots`](@ref)
