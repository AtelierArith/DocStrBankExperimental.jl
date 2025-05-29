```
nestedview(A::AbstractArray{T,M+N}, M::Integer)
nestedview(A::AbstractArray{T,2})
```

AbstractArray{<:AbstractArray{T,M},N}

View array `A` in as an `N`-dimensional array of `M`-dimensional arrays by wrapping it into an [`ArrayOfSimilarArrays`](@ref).

It's also possible to use a `StaticVector` of length `S` as the type of the inner arrays via

```
nestedview(A::AbstractArray{T}, ::Type{StaticArrays.SVector{S}})
nestedview(A::AbstractArray{T}, ::Type{StaticArrays.SVector{S,T}})
```
