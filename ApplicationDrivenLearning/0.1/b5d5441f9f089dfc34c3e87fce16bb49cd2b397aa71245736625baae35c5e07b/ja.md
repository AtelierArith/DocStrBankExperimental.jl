```
PredictiveModel(networks::Flux.Chain, input_output_map::Dict{Vector{Int}, Vector{Int}})
```

Chainオブジェクトとして1つのネットワークのみが渡され、明示的な入力から出力へのマッピングがある場合、入力サイズと出力サイズは直接抽出されます。
