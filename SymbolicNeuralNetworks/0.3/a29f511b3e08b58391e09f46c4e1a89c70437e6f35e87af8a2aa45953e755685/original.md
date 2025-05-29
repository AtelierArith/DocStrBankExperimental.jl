```
build_nn_function(eqs::Union{NamedTuple, NeuralNetworkParameters}, sparams, sinput...)
```

Return a function that takes an input, (optionally) an output and neural network parameters and returns a `NeuralNetworkParameters`-valued output.

# Examples

```jldoctest
using SymbolicNeuralNetworks: build_nn_function, SymbolicNeuralNetwork
using AbstractNeuralNetworks: Chain, Dense, NeuralNetwork, params
import Random
Random.seed!(123)

c = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(c)
snn = SymbolicNeuralNetwork(nn)
eqs = (a = c(snn.input, params(snn)), b = c(snn.input, params(snn)).^2)
funcs = build_nn_function(eqs, params(snn), snn.input)
input = [1., 2.]
funcs_evaluated = funcs(input, params(nn))

# output

(a = [0.985678060655224], b = [0.9715612392570434])
```

# Implementation

Internally this is using [`function_valued_parameters`](@ref) and [`apply_element_wise`](@ref).
