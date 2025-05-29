```
build_nn_function(eqs::Union{NamedTuple, NeuralNetworkParameters}, sparams, sinput...)
```

入力を受け取り、（オプションで）出力とニューラルネットワークパラメータを受け取り、`NeuralNetworkParameters`型の出力を返す関数を返します。

# 例

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

# 出力

(a = [0.985678060655224], b = [0.9715612392570434])
```

# 実装

内部では[`function_valued_parameters`](@ref)と[`apply_element_wise`](@ref)を使用しています。
