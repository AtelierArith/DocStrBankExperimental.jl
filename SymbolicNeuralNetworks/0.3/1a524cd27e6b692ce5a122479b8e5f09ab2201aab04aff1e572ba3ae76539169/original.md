```
SymbolicNeuralNetwork <: AbstractSymbolicNeuralNetwork
```

A symbolic neural network realizes a symbolic represenation (of small neural networks).

# Fields

The `struct` has the following fields:

  * `architecture`: the neural network architecture,
  * `model`: the model (typically a Chain that is the realization of the architecture),
  * `params`: the symbolic parameters of the network.
  * `sinput`: the symbolic input of the network.

# Constructors

```
SymbolicNeuralNetwork(nn)
```

Make a `SymbolicNeuralNetwork` based on a `AbstractNeuralNetworks.Network`.
