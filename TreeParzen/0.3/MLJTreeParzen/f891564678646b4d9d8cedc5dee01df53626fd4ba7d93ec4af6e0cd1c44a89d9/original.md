```julia
MLJTreeParzenSpace(
    input_space::Dict{Symbol},
    suggestion::Dict{Symbol}
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenSpace

```

As above, but also accepting `suggestion` with parameter names and specific values to evaluate the function to be tuned with.

The default constructor accepts a vector of suggestions.

Example (single suggestion):

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    ),
    Dict(:num_layers => 3, :num_nodes => 40.0)
);
```

Example (multiple suggestions):

```julia
using TreeParzen

search = MLJTreeParzen.MLJTreeParzenSpace(
    Dict(
        :num_layers => HP.Choice(:num_layers, [2, 3, 4]),
        :num_nodes => HP.QuantUniform(:num_nodes, 20.0, 50.0, 1.0),
    ),
    [
        Dict(:num_layers => 3, :num_nodes => 40.0),
        Dict(:num_layers => 3, :num_nodes => 30.0),
    ]
);
```
