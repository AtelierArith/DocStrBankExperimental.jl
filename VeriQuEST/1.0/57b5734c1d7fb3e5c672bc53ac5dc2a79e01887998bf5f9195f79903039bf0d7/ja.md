```
create_graph_resource(p::NamedTuple)::MBQCResourceState
```

NamedTuple `p` から `MBQCResourceState` を作成します。NamedTuple には以下のキーが含まれている必要があります: `input_indices`, `input_values`, `output_indices`, `computation_colours`, `test_colours`, `graph`, `forward_flow`, `backward_flow`, および `secret_angles`。

# 引数

  * `p`: `MBQCResourceState` を作成するために必要なパラメータを含む NamedTuple。

# 例

```julia
params = (input_indices = ..., input_values = ..., output_indices = ..., computation_colours = ..., test_colours = ..., graph = ..., forward_flow = ..., backward_flow = ..., secret_angles = ...)
resource = create_graph_resource(params)
```
