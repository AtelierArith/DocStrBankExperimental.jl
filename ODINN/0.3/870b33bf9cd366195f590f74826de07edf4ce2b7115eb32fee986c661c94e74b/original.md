```
NeuralNetwork{
    ChainType <: Lux.Chain,
    ComponentVectorType <: ComponentVector,
    NamedTupleType <: NamedTuple
} <: MLmodel
```

Feed-forward neural network.

# Fields

  * `architecture::ChainType`: `Flux.Chain` neural network architecture
  * `θ::ComponentVectorType`: Neural network parameters
  * `st::NamedTupleType`: Neural network status
