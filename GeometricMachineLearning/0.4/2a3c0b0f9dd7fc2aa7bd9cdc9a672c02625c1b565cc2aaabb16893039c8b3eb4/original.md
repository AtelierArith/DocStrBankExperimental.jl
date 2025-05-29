```
ReducedLoss(encoder, decoder)
```

Make an instance of `ReducedLoss` based on an [`Encoder`](@ref) and a [`Decoder`](@ref).

This loss should be used together with a [`NeuralNetworkIntegrator`](@ref) or [`TransformerIntegrator`](@ref).

# Example

`ReducedLoss` applies the *encoder*, *integrator* and *decoder* neural networks in this order to an input and compares it to the `output` via an $L_2$ norm:

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

So the loss computes: 

$$
\mathrm{loss}_{\mathcal{E}, \mathcal{D}}(\mathcal{NN}, \mathrm{input}, \mathrm{output}) = ||\mathcal{D}(\mathcal{NN}(\mathcal{E}(\mathrm{input}))) - \mathrm{output}||,
$$

where $\mathcal{E}$ is the [`Encoder`](@ref), $\mathcal{D}$ is the [`Decoder`](@ref). $\mathcal{NN}$ is the neural network we compute the loss of.
