```
settypes!(lines::LineIndex, rows::Union{UnitRange{Int}, Vector{Int}} = 1:5)
```

選択された `rows` に基づいて `lines` の列の型を推論します。既存の型を上書きします。
