```
create_graph_resource(p::NamedTuple)::MBQCResourceState
```

Creates an `MBQCResourceState` from a NamedTuple `p`. The NamedTuple should contain the following keys: `input_indices`, `input_values`, `output_indices`, `computation_colours`, `test_colours`, `graph`, `forward_flow`, `backward_flow`, and `secret_angles`.

# Arguments

  * `p`: A NamedTuple containing the necessary parameters to create an `MBQCResourceState`.

# Examples

```julia
params = (input_indices = ..., input_values = ..., output_indices = ..., computation_colours = ..., test_colours = ..., graph = ..., forward_flow = ..., backward_flow = ..., secret_angles = ...)
resource = create_graph_resource(params)
```
