```
solution_statuses!(pm::AbstractUnbalancedPowerModel, sol::Dict{String,Any})
```

解決策 `sol` のすべての `status` フィールドを Float64 から `Status` 列挙型に変換します。すべての時間ステップに対して。
