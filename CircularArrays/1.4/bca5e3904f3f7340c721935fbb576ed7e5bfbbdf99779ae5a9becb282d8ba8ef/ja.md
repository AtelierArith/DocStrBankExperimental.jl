```
CircularArray{T, N, A} <: AbstractArray{T, N}
```

`N`次元配列で、固定サイズと循環インデックスを持つ型`A`の`AbstractArray{T, N}`に基づいています。

```
array[index...] == array[mod1.(index, size)...]
```
