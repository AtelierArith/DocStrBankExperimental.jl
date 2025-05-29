```
SymbolicPullback(arch::HamiltonianArchitecture)
```

Make a `SymbolicPullback` based on a [`HamiltonianArchitecture`](@ref).

# Implementation

Internally this is calling `SymbolicNeuralNetwork` and [`HNNLoss`](@ref).
