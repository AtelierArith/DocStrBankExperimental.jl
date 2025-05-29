```
HNNLoss <: NetworkLoss
```

The loss for a Hamiltonian neural network.

# Constructor

This can be called with a `NeuralNetwork`, built with a [`HamiltonianArchitecture`](@ref), as the only input arguemtn, i.e.:

```julia
HNNLoss(nn)
```

where `nn` is a `NeuralNetwork`, that is built with a [`HamiltonianArchitecture`](@ref), gives the corresponding Hamiltonian loss.

# Functor

```julia
loss(c, ps, input, output)
loss(ps, input, output) # equivalent to the above
```
