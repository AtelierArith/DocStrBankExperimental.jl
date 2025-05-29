```
make_layer(gate_type::String, range::Vector{Int}, n::Integer; index::Integer = 0)
```

指定された `range` の量子ビットに作用する単一量子ビット `gate_type` ゲートのレイヤーを返します。このレイヤーは `n` 個の量子ビットに作用し、オプションでゲートインデックス `index` を指定できます。
