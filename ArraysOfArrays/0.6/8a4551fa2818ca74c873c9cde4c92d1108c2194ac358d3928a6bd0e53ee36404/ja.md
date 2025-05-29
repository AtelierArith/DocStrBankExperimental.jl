```
nestedview(A::AbstractArray{T,M+N}, M::Integer)
nestedview(A::AbstractArray{T,2})
```

AbstractArray{<:AbstractArray{T,M},N}

配列 `A` を `M` 次元配列の `N` 次元配列として表示するには、[`ArrayOfSimilarArrays`](@ref) にラップします。

内部配列の型として長さ `S` の `StaticVector` を使用することも可能です。

```
nestedview(A::AbstractArray{T}, ::Type{StaticArrays.SVector{S}})
nestedview(A::AbstractArray{T}, ::Type{StaticArrays.SVector{S,T}})
```
