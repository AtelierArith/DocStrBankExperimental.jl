```
HNNLoss <: NetworkLoss
```

ハミルトンニューラルネットワークの損失。

# コンストラクタ

これは、唯一の入力引数として[`HamiltonianArchitecture`](@ref)で構築された`NeuralNetwork`を使って呼び出すことができます。すなわち：

```julia
HNNLoss(nn)
```

ここで`nn`は、[`HamiltonianArchitecture`](@ref)で構築された`NeuralNetwork`であり、対応するハミルトン損失を与えます。

# ファンクタ

```julia
loss(c, ps, input, output)
loss(ps, input, output) # 上記と同等
```
