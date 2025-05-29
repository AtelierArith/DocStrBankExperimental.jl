```
generate_load_scenarios(data::Dict{String,<:Any}, N::Int, ΔL::Float64)::Dict{Int,Dict{Any,Any}}
```

基準負荷の周りに±ΔLの不確実性を持つNシナリオを生成します。最初のシナリオは常に基準負荷を使用します。PMD.solve*mc*opf()は、元の問題に対して実行可能かどうかを確認するために各シナリオで解かれます（`data`はマイクログリッドのないネットワークであり、すべてのブロックは変電所によって電力供給されています）。
