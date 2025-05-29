```
get_gate_data(total_gates::Vector{Gate}; combined::Bool = false, strict::Bool = false)
```

ゲート `total_gates` のゲートデータを [`GateData`](@ref) オブジェクトの形式で返します。`combined` が `true` の場合は、パウリ X、Y、および Z 基準の SPAM ノイズを組み合わせ、`strict` が `true` の場合は、どのゲートが加算的または相対的精度で推定可能と見なされるかに厳密になります。
