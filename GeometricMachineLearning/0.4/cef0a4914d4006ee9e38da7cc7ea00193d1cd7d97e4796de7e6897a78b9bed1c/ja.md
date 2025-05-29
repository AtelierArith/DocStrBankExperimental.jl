```
LinearSymplecticTransformer(sys_dim, seq_length)
```

特定のシステム次元とシーケンス長のために `LinearSymplecticTransformer` のインスタンスを作成します。

# 引数

追加のオプションキーワード引数を提供できます：

  * `n_sympnet::Int = (2)`: トランスフォーマー内のsympnet層の数。
  * `upscaling_dimension::Int = 2*dim`: 勾配層によって行われるアップスケーリング。
  * `L::Int = 1`: トランスフォーマーユニットの数。
  * `activation = tanh`: SympNet層のための活性化関数。
  * `init_upper::Bool=true`: 最初の層が$q$型層（`init_upper=true`）であるか、$p$型層（`init_upper=false`）であるかを指定します。

ネットワーク内のSympNet層の数は `2n_sympnet` であり、すなわち `n_sympnet = 1` の場合、1つの [`GradientLayerQ`](@ref) と1つの [`GradientLayerP`](@ref) があります。
