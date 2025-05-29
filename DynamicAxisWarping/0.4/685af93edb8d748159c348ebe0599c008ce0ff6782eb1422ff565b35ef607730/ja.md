```
struct DTW{D,N} <: DTWDistance{D}
```

# キーワード引数:

  * `radius`: 対角線からのマッチングパスの最大許容偏差
  * `dist`: 内部距離
  * `transportcost`: 1より大きい場合、非対角移動に対する追加のペナルティ係数が加算されます。
  * `normalizer`: デフォルトは `Nothing`。サポートされているオプションは、[SlidingDistancesBase.jl](https://github.com/baggepinnen/SlidingDistancesBase.jl)で定義された正規化器です。

2つの時系列が同じ長さの場合、[`dtw_cost`](@ref)が呼び出され、そうでない場合は[`dtwnn`](@ref)が呼び出されます。
