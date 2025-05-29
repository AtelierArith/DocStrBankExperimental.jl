```
optimal_dimension(v, τ; dims = 2:8; method = "fnn"; kwargs...)
```

`v`の最適埋め込み次元を推定します。

## 引数

  * **`v`**: 埋め込み次元を推定するデータ系列。
  * **`τ`**: 埋め込みラグ。
  * **`dims`**: 最適次元を探るための次元。

## キーワード引数

  * **`method`**: "fnn"（ケネルの偽最近接近法）、"afnn"（カオの平均偽最近接近法）または "f1nn"（クラコフスカーの偽第一最近接近法）のいずれか。詳細については、`DelayEmbeddings.estimate_dimension`のソースコードを参照してください。
  * **`rtol`**: ケネルのアルゴリズムにおける許容誤差`rtol`。詳細については[`DelayEmbeddings.fnn`](https://github.com/JuliaDynamics/DelayEmbeddings.jl/blob/master/src/estimate_dimension.jl)のソースコードを参照してください。
  * **`atol`**: ケネルのアルゴリズムにおける許容誤差`rtol`。詳細については[`DelayEmbeddings.fnn`](https://github.com/JuliaDynamics/DelayEmbeddings.jl/blob/master/src/estimate_dimension.jl)のソースコードを参照してください。
