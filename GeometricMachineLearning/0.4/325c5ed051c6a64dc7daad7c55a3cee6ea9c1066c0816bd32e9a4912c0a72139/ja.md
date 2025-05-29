```
GeneralizedHamiltonianArchitecture <: HamiltonianArchitecture
```

一般化ハミルトン神経ネットワーク（GHNN）の実現であり、[horn2025generalized](@cite)で紹介されています。

また、[`StandardHamiltonianArchitecture`](@ref)も参照してください。

# コンストラクタ

コンストラクタは以下の入力引数を取ります：

1. `dim`: システムの次元、
2. `width = dim`: 隠れ層の幅。デフォルトでは`dim`と等しいです、
3. `nhidden = 1`: 隠れ層の数、
4. `activation = AbstractNeuralNetworks.TanhActivation()`: GHNNで使用される活性化関数、
5. `integrator = nothing`: GHNNを設計するために使用される積分器。
