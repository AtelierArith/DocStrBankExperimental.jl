```
Bravais.DirectBasis{D, E} <: AbstractBasis{D, E}
```

`D` 個の異なる `D` 次元ベクトル（`SVector{D, SVector{D, E}}` として与えられる）をラッパータイプとして、直接空間における格子基底を定義します。デフォルトでは（省略した場合）、`E` は `Float64` です。
