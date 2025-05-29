```
StandardHamiltonianArchitecture <: HamiltonianArchitecture
```

標準ハミルトンニューラルネットワーク (HNN) [greydanus2019hamiltonian](@cite) の実現です。

また、[`GeneralizedHamiltonianArchitecture`](@ref) も参照してください。

# コンストラクタ

コンストラクタは以下の入力引数を取ります：

1. `dim`: システムの次元、
2. `width = dim`: 隠れ層の幅。デフォルトでは `dim` と等しいです、
3. `nhidden = 1`: 隠れ層の数、
4. `activation = AbstractNeuralNetworks.TanhActivation()`: HNNで使用される活性化関数。
