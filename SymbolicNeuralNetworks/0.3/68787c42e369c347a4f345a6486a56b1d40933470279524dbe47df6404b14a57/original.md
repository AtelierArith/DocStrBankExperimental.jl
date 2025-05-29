```
build_nn_function(eqs::AbstractArray{<:NeuralNetworkParameters}, sparams, sinput...)
```

Build an executable function based on an array of symbolic equations `eqs`.

# Examples

```jldoctest
using SymbolicNeuralNetworks: build_nn_function, SymbolicNeuralNetwork
using AbstractNeuralNetworks: Chain, Dense, NeuralNetwork, params
import Random
Random.seed!(123)

ch = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(ch)
snn = SymbolicNeuralNetwork(nn)
eqs = [(a = ch(snn.input, params(snn)), b = ch(snn.input, params(snn)).^2), (c = ch(snn.input, params(snn)).^3, )]
funcs = build_nn_function(eqs, params(snn), snn.input)
input = [1., 2.]
funcs_evaluated = funcs(input, params(nn))

# output

2-element Vector{NamedTuple}:
 (a = [0.985678060655224], b = [0.9715612392570434])
 (c = [0.9576465981186686],)
```
