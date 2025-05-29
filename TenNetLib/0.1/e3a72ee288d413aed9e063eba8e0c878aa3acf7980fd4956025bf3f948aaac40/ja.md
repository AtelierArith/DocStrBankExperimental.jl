```
function move_linktensors!(env::LinkTensorsTTN, psi::TTN,
                           source_node::Int2,
                           destination_node::Int2;
                           kwargs...)::Nothing
```

`source_node`から`destination_node`へ環境テンソルを移動します。
