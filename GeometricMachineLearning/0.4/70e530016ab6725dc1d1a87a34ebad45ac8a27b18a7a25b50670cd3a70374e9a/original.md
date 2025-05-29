```
StandardHamiltonianArchitecture <: HamiltonianArchitecture
```

A realization of the standard Hamiltonian neural network (HNN) [greydanus2019hamiltonian](@cite).

Also see [`GeneralizedHamiltonianArchitecture`](@ref).

# Constructor

The constructor takes the following input arguments:

1. `dim`: system dimension,
2. `width = dim`: width of the hidden layer. By default this is equal to `dim`,
3. `nhidden = 1`: the number of hidden layers,
4. `activation = AbstractNeuralNetworks.TanhActivation()`: the activation function used in the HNN.
