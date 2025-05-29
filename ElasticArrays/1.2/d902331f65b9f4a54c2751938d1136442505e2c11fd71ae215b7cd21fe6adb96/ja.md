```
ElasticArray{T,N,M} <: DenseArray{T,N}
```

`ElasticArray`は最後の次元で成長/縮小することができます。`N`は次元の総数、`M == N - 1`はサイズ変更できない次元の数です。

コンストラクタ:

```
ElasticArray{T}(dims::Integer...)
convert(ElasticArray, A::AbstractArray)
```
