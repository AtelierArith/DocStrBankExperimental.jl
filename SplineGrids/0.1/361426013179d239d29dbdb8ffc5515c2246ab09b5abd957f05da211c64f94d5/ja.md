```
mult!(
    Y::V,
    As::NTuple{<:RefinementMatrix{Tv}, N},
    B::V,
    dims_refinement::NTuple{<:Integer, N})::Nothing where {Tv, V <: AbstractArray{Tv}, N}
```

配列 B を指定された次元に沿ってすべてのリファインメント行列で「左乗算」します。

## 入力

  * `Y`: 乗算の対象となる配列
  * `As`: `Y` が乗算されるリファインメント行列
  * `B`: リファインメント行列で乗算される配列
  * `dims_refinement`: 各行列のリファインメント行列乗算が行われる次元
