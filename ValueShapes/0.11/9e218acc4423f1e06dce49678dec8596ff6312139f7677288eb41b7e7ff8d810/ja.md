```
ArrayShape{T,N} <: AbstractValueShape
```

は、型 `T` の `N` 次元配列の形状と指定されたサイズを表します。

コンストラクタ:

```
ArrayShape{T}(dims::NTuple{N,Integer}) where {T,N}
ArrayShape{T}(dims::Integer...) where {T}
```

例:

```
shape = ArrayShape{Real}(2, 3)
```

[`AbstractValueShape`](@ref) のドキュメントも参照してください。
