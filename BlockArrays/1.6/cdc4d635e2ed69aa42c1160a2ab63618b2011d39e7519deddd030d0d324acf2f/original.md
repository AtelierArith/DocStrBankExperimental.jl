```
abstract AbstractBlockArray{T, N} <: AbstractArray{T, N}
```

The abstract type that represents a blocked array. Types that implement the `AbstractBlockArray` interface should subtype from this type.

** Typealiases **

  * `AbstractBlockMatrix{T}` -> `AbstractBlockArray{T, 2}`
  * `AbstractBlockVector{T}` -> `AbstractBlockArray{T, 1}`
  * `AbstractBlockVecOrMat{T}` -> `Union{AbstractBlockMatrix{T}, AbstractBlockVector{T}}`
