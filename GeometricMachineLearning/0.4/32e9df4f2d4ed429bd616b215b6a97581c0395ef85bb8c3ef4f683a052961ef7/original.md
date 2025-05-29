```
AutoEncoderLoss()
```

Make an instance of `AutoEncoderLoss`.

This loss should always be used together with a neural network of type [`AutoEncoder`](@ref) (and it is also the default for training such a network). 

# Example

`AutoEncoderLoss` applies a neural network to an input and compares it to the `output` via an $L_2$ norm:

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random
Random.seed!(123)

const N = 4
const n = 1
arch = SymplecticAutoencoder(2*N, 2*n)
nn = NeuralNetwork(arch)

input_vec =  [1., 2., 3., 4., 5., 6., 7., 8.]
loss = AutoEncoderLoss()

loss(nn, input_vec) ≈ norm(input_vec - nn(input_vec)) / norm(input_vec)

# output

true
```

So `AutoEncoderLoss` simply does:

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}) = || \mathcal{NN}(\mathtt{input}) - \mathtt{input} || / || \mathtt{input} ||,
$$

where $||\cdot||$ is the $L_2$ norm. 

# Parameters

This loss does not have any parameters.
