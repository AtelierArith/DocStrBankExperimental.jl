```
GeneralizedHamiltonianArchitecture <: HamiltonianArchitecture
```

A realization of generalized Hamiltonian neural networks (GHNNs) as introduced in [horn2025generalized](@cite).

Also see [`StandardHamiltonianArchitecture`](@ref).

# Constructor

The constructor takes the following input arguments:

1. `dim`: system dimension,
2. `width = dim`: width of the hidden layer. By default this is equal to `dim`,
3. `nhidden = 1`: the number of hidden layers,
4. `activation = AbstractNeuralNetworks.TanhActivation()`: the activation function used in the GHNN,
5. `integrator = nothing`: the integrator that is used to design the GHNN.
