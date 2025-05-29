```
function move_linktensors!(env::LinkTensorsTTN, psi::TTN,
                           source_node::Int2,
                           destination_node::Int2;
                           kwargs...)::Nothing
```

Moves the environment tensors from `source_node` to `destination_node`.
