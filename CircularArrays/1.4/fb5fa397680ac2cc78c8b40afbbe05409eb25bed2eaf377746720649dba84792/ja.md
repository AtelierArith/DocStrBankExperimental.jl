```
CircularVector{T,A} <: AbstractVector{T}
```

固定サイズと循環インデックスを持つ `AbstractArray{T, 1}` 型 `A` に基づく一次元配列。 [`CircularArray{T,1,A}`](@ref) のエイリアスです。

```
array[index] == array[mod1(index, length)]
```
