```julia
MLJTreeParzenSpace(
    input_space::Dict{Symbol}
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenSpace

```

Construct a hyperparameter search space from a `input_space` with keys as parameter names and values as `TreeParzen.HP.*` tunable distributions (or composite expressions of these).

Example:

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    )
);
```
