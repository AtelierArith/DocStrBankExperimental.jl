```
SymbolicNeuralNetwork <: AbstractSymbolicNeuralNetwork
```

シンボリックニューラルネットワークは、シンボリックな表現（小さなニューラルネットワークの）を実現します。

# フィールド

`struct` には以下のフィールドがあります：

  * `architecture`: ニューラルネットワークのアーキテクチャ、
  * `model`: モデル（通常はアーキテクチャの実現であるChain）、
  * `params`: ネットワークのシンボリックパラメータ。
  * `sinput`: ネットワークのシンボリック入力。

# コンストラクタ

```
SymbolicNeuralNetwork(nn)
```

`AbstractNeuralNetworks.Network` に基づいて `SymbolicNeuralNetwork` を作成します。
