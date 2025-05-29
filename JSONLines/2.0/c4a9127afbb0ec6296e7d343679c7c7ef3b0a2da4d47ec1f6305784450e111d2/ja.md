```
materialize(lines::LineIndex,  f::Function, rows::Union{UnitRange{Int}, Vector{Int}} = 1:length(lines); eltype = T where T)
```

選択された `rows` に `f` を適用します。結果の `eltype` はキーワード引数として指定できます。
