```
make_layer(gate_type::String, range_set::Vector{Vector{Int}}, n::Integer; index::Integer = 0)
```

`gate_type` ゲートのレイヤーを返します。各ゲートは `range_set` の量子ビットに作用し、レイヤーは `n` 個の量子ビットに作用します。オプションでゲートインデックス `index` を指定できます。
