```
ReducedLoss(encoder, decoder)
```

[`Encoder`](@ref) と [`Decoder`](@ref) に基づいて `ReducedLoss` のインスタンスを作成します。

この損失は、[`NeuralNetworkIntegrator`](@ref) または [`TransformerIntegrator`](@ref) と一緒に使用する必要があります。

# 例

`ReducedLoss` は、入力に対して *encoder*、*integrator*、*decoder* ニューラルネットワークをこの順序で適用し、$L_2$ ノルムを介して `output` と比較します：

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random
Random.seed!(123)

const N = 4
const n = 1

Ψᵉ = NeuralNetwork(Chain(Dense(N, n), Dense(n, n))) |> encoder
Ψᵈ = NeuralNetwork(Chain(Dense(n, n), Dense(n, N))) |> decoder
transformer = NeuralNetwork(StandardTransformerIntegrator(n))

input_mat =  [1.  2.;  3.  4.;  5.  6.;  7.  8.]
output_mat = [9. 10.; 11. 12.; 13. 14.; 15. 16.]
loss = ReducedLoss(Ψᵉ, Ψᵈ)

output_prediction = Ψᵈ(transformer(Ψᵉ(input_mat)))
loss(transformer, input_mat, output_mat) ≈ norm(output_mat - output_prediction) / norm(output_mat)

# output

true
```

したがって、損失は次のように計算されます：

$$
\mathrm{loss}_{\mathcal{E}, \mathcal{D}}(\mathcal{NN}, \mathrm{input}, \mathrm{output}) = ||\mathcal{D}(\mathcal{NN}(\mathcal{E}(\mathrm{input}))) - \mathrm{output}||,
$$

ここで、$\mathcal{E}$ は [`Encoder`](@ref)、$\mathcal{D}$ は [`Decoder`](@ref) です。$\mathcal{NN}$ は損失を計算するニューラルネットワークです。
