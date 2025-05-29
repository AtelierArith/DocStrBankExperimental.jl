```
StencilRecurrence{N,T,S,
    COEF<:NTuple{S,AbstractArray{T,N}},
    TB<:AbstractArray{T,N},}
    (stencil, coef, buffer, slicestart, sliceend, lastind)
```

# Parameters

  * `N`: system dimension
  * `T`: eltype
  * `S`: stencil size

# Properties

For `coef` and `slicesupport`, tt's suggested to use lazy arrays for performance.

  * `stencil::NTuple{S, CartesianIndex{N}}`: The relative index of the stencil. Can contain `(0,0)` (see `coef`)
  * `coef::COEF<:NTuple{S,AbstractArray{T,N}}`: The coefficient associated with each relative index. The one associated with `CartesianIndex(0,0)` refers to a constant added to that entry. It's suggested to use lazy arrays for performance.
  * `buffer::CircularArray{T,N,TB<:AbstractArray{T,N}}`: a buffer to store temp results.
  * `slicestart::MVector{N, Int}` and `sliceend::MVector{N, Int}`: marks the current range of entries to be determined. Technically `NTuple{N-1, Int}` should work, but `Julia` doesn't support computed type parameters.
  * `lastslice::Int`: marks the index of the slice where the recurrence terminates.
