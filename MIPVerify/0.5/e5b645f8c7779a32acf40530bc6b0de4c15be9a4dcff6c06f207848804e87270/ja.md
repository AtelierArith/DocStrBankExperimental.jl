```julia
struct SkipSequential <: MIPVerify.NeuralNet
```

入力から出力まで順序付けられた層を持つ順次（フィードフォワード）ニューラルネットを表します。通常の`Sequential`ネットワークとは異なり、このネットワークタイプは[`SkipBlock`](@ref)をサポートしており、複数の前の層からの入力を受け取ることができます。`SkipBlock`に遭遇すると、それは前の層からの出力の配列を受け取り、スキップ接続や残差アーキテクチャを可能にします。

## フィールド:

  * `layers`
  * `UUID`
