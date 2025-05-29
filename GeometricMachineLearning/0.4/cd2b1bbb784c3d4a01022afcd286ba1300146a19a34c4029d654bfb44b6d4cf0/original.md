```
LASympNet(d)
```

Make an $LA$-SympNet with dimension $d.$

There exists an additional constructor that can be called by supplying an instance of [`DataLoader`](@ref).

# Examples

```jldoctest
using GeometricMachineLearning
dl = DataLoader(rand(2, 20); suppress_info = true)
LASympNet(dl)

# output

LASympNet{typeof(tanh), true, true}(2, 5, 1, tanh)
```

# Arguments

Keyword arguments are: 

  * `depth::Int = 5`: The number of linear layers that are applied.
  * `nhidden::Int = 1`: The number of hidden layers (i.e. layers that are *not* output layers).
  * `activation = tanh`: The activation function that is applied.
  * `init_upper_linear::Bool = true`: Initialize the linear layer so that it first modifies the $q$-component.
  * `init_upper_act::Bool = true`: Initialize the activation layer so that it first modifies the $q$-component.
