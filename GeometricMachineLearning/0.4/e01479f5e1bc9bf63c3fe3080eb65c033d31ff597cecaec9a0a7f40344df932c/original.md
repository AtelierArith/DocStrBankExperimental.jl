```
iterate(nn, ics)
```

This function computes a trajectory for a [`NeuralNetworkIntegrator`](@ref) that has already been trained for valuation purposes.

It takes as input: 

1. `nn`: a `NeuralNetwork` (that has been trained).
2. `ics`: initial conditions (a `NamedTuple` of two vectors)

# Examples

To demonstrate `iterate` we use a simple ResNet that does:

$$
\mathrm{ResNet}: x \mapsto \begin{pmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 1\end{pmatrix}x + \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
$$

and we iterate three times with

$$
    \mathtt{ics} = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}.
$$

```jldoctest
using GeometricMachineLearning

model = ResNet(3, 0, identity)
weight = [1 0 0; 0 2 0; 0 0 1]
bias = [0, 0, 1]
ps = NeuralNetworkParameters((L1 = (weight = weight, bias = bias), ))
nn = NeuralNetwork(model, Chain(model), ps, CPU())

ics = [1, 1, 1]
iterate(nn, ics; n_points = 4)

# output

3×4 Matrix{Int64}:
 1  2  4   8
 1  3  9  27
 1  3  7  15
```

# Arguments

The optional keyword argument is 

  * `n_points = 100`

The number of integration steps that should be performed.
