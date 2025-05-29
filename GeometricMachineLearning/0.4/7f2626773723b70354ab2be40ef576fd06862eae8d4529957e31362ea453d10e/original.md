```
FeedForwardLoss()
```

Make an instance of a loss for feedforward neural networks.

This should be used together with a neural network of type [`NeuralNetworkIntegrator`](@ref).

# Example

`FeedForwardLoss` applies a neural network to an input and compares it to the `output` via an $L_2$ norm:

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random
Random.seed!(123)

const d = 2
arch = GSympNet(d)
nn = NeuralNetwork(arch)

input_vec =  [1., 2.]
output_vec = [3., 4.]
loss = FeedForwardLoss()

loss(nn, input_vec, output_vec) ≈ norm(output_vec - nn(input_vec)) / norm(output_vec)

# output

true
```

So `FeedForwardLoss` simply does:

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}, \mathtt{output}) = || \mathcal{NN}(\mathtt{input}) - \mathtt{output} || / || \mathtt{output}||,
$$

where $||\cdot||$ is the $L_2$ norm. 

# Parameters

This loss does not have any parameters.
