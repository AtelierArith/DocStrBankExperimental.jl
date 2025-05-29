```
SymplecticTransformer <: TransformerIntegrator
```

# コンストラクタ

```julia
SymplecticTransformer(sys_dim)
```

特定のシステム次元とシーケンス長のために `SymplecticTransformer` のインスタンスを作成します。 [`LinearSymplecticTransformer`](@ref) も参照してください。

# 引数

追加のオプションキーワード引数を提供できます：

  * `n_sympnet::Int = (2)`: トランスフォーマー内のシンプレクティックネット層の数。
  * `upscaling_dimension::Int = 2*dim`: 勾配層によって行われるアップスケーリング。
  * `L::Int = 1`: トランスフォーマーユニットの数。
  * `sympnet_activation = tanh`: SympNet層のための活性化関数。
  * `attention_activation = GeometricMachineLearning.MatrixSoftmax()`: アテンション層のための活性化関数。
  * `init_upper::Bool=true`: 最初の層が $q$-型層（`init_upper=true`）であるか、$p$-型層（`init_upper=false`）であるかを指定します。
  * `symmetric::Bool=false`:

ネットワーク内のSympNet層の数は `2n_sympnet` です。つまり、`n_sympnet = 1` の場合、1つの [`GradientLayerQ`](@ref) と1つの [`GradientLayerP`](@ref) があります。
