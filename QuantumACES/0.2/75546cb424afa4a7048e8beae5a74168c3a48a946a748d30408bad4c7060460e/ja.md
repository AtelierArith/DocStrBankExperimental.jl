```
init_gate_probabilities(total_gates::Vector{Gate}, dep_param::DepolarisingParameters)
```

`dep_param`に従って生成された`total_gates`内の各ゲートのパウリ誤差確率の辞書を返します。これは[`get_paulis`](@ref)に従って辞書順に並べられています。
