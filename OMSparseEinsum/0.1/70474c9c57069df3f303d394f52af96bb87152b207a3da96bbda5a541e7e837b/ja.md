```
SparseTensor{Tv,Ti,N} <: AbstractSparseArray{Tv, Ti, N}
```

スパーステンソルは、スパース形式で保存される多次元配列です。

# フィールド

  * `size::NTuple{N, Int}`: テンソルのサイズ
  * `strides::NTuple{N, Ti}`: テンソルのストライド
  * `data::Dict{Ti, Tv}`: テンソルのデータ
