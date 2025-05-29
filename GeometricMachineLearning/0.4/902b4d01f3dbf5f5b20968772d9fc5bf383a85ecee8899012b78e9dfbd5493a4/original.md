```
TransformerLoss(seq_length, prediction_window)
```

Make an instance of the transformer loss. 

This should be used together with a neural network of type [`TransformerIntegrator`](@ref).

# Example

`TransformerLoss` applies a neural network to an input and compares it to the `output` via an $L_2$ norm:

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random

const d = 2
const seq_length = 3
const prediction_window = 2

Random.seed!(123)
arch = StandardTransformerIntegrator(d)
nn = NeuralNetwork(arch)

input_mat =  [1. 2. 3.; 4. 5. 6.]
output_mat = [1. 2.; 3. 4.]
loss = TransformerLoss(seq_length, prediction_window)

# start of prediction
const sop = seq_length - prediction_window + 1
loss(nn, input_mat, output_mat) ≈ norm(output_mat - nn(input_mat)[:, sop:end]) / norm(output_mat)

# output

true
```

So `TransformerLoss` simply does:

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}, \mathtt{output}) = || \mathcal{NN}(\mathtt{input})[(\mathtt{sl} - \mathtt{pw} + 1):\mathtt{end}] - \mathtt{output} || / || \mathtt{output} ||,
$$

where $||\cdot||$ is the $L_2$ norm. 

# Parameters

The `prediction_window` specifies how many time steps are predicted into the future. It defaults to the value specified for `seq_length`.
