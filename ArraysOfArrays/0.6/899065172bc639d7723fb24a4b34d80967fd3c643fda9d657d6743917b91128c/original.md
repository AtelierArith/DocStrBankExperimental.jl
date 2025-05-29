```
AbstractArrayOfSimilarArrays{T,M,N} <: AbstractArray{<:AbstractArray{T,M},N}
```

An array that contains arrays that have the same size/axes. The array is internally stored in flattened form as some kind of array of dimension `M + N`. The flattened form can be accessed via `flatview(A)`.

Subtypes must implement (in addition to typical array operations):

```
flatview(A::SomeArrayOfSimilarArrays)::AbstractArray{T,M+N}
```

The following type aliases are defined:

  * `AbstractVectorOfSimilarArrays{T,M} = AbstractArrayOfSimilarArrays{T,M,1}`
  * `AbstractArrayOfSimilarVectors{T,N} = AbstractArrayOfSimilarArrays{T,1,N}`
  * `AbstractVectorOfSimilarVectors{T} = AbstractArrayOfSimilarArrays{T,1,1}`
