```
NeuralNetwork{
    ChainType <: Lux.Chain,
    ComponentVectorType <: ComponentVector,
    NamedTupleType <: NamedTuple
} <: MLmodel
```

フィードフォワードニューラルネットワーク。

# フィールド

  * `architecture::ChainType`: `Flux.Chain` ニューラルネットワークアーキテクチャ
  * `θ::ComponentVectorType`: ニューラルネットワークパラメータ
  * `st::NamedTupleType`: ニューラルネットワークの状態
