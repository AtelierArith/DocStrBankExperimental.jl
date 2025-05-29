```
ScaledArray{T,R,N,RA,P} <: AbstractArray{T,N}
```

Array type that stores data as indices of a range.

# Fields

  * `refs::RA<:AbstractArray{R,N}`: an array of indices.
  * `pool::P<:AbstractRange`: a range that covers all possible values stored by the array.
  * `invpool::Dict{T,R}`: a map from array elements to indices of `pool`.
