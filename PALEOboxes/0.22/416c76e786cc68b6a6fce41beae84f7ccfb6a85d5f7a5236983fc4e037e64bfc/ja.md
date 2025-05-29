```
check_data_type(existing_values, data_type::Union{Missing, Type})
```

[`check_values`](@ref) 実装のためのヘルパー関数: `existing_values` が `data_type`（指定されている場合）と一貫しているかを確認し、一貫していない場合は例外をスローします。
