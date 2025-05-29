```
ArrayOfSimilarArrays{T,M,N,L,P} <: AbstractArrayOfSimilarArrays{T,M,N}
```

Represents a view of an array of dimension `L = M + N` as an array of dimension M with elements that are arrays with dimension N. All element arrays implicitly have equal size/axes.

Constructors:

```
ArrayOfSimilarArrays{T,M,N}(flat_data::AbstractArray)
ArrayOfSimilarArrays{T,M}(flat_data::AbstractArray)
```

The following type aliases are defined:

  * `VectorOfSimilarArrays{T,M} = AbstractArrayOfSimilarArrays{T,M,1}`
  * `ArrayOfSimilarVectors{T,N} = AbstractArrayOfSimilarArrays{T,1,N}`
  * `VectorOfSimilarVectors{T} = AbstractArrayOfSimilarArrays{T,1,1}`

`VectorOfSimilarArrays` supports `push!()`, etc., provided the underlying array supports resizing of it's last dimension (e.g. an `ElasticArray`).

The nested array can also be created using the function [`nestedview`](@ref) and the wrapped flat array can be accessed using [`flatview`](@ref) afterwards:

```julia
A_flat = rand(2,3,4,5,6)
A_nested = nestedview(A_flat, 2)
A_nested isa AbstractArray{<:AbstractArray{T,2},3} where T
flatview(A_nested) === A_flat
```
