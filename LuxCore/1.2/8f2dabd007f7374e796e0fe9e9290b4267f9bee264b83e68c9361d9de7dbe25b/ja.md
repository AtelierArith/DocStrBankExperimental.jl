```
abstract type AbstractLuxLayer
```

すべてのLuxレイヤーのための抽象型

ユーザーがカスタムレイヤーを実装する際には、**必ず**以下を実装する必要があります。

  * `initialparameters(rng::AbstractRNG, layer::CustomAbstractLuxLayer)` – これはレイヤーの学習可能なパラメータを含む`NamedTuple`を返します。
  * `initialstates(rng::AbstractRNG, layer::CustomAbstractLuxLayer)` – これはレイヤーの現在の状態を含むNamedTupleを返します。ほとんどのレイヤーでは、これは通常空です。これを含む可能性のあるレイヤーには、`BatchNorm`、`LSTM`、`GRU`などがあります。

オプションとして：

  * `parameterlength(layer::CustomAbstractLuxLayer)` – これらは自動的に計算できますが、ユーザーが定義することを推奨します。
  * `statelength(layer::CustomAbstractLuxLayer)` – これらも自動的に計算できますが、ユーザーが定義することを推奨します。

詳細については、[`AbstractLuxContainerLayer`](@ref)を参照してください。
