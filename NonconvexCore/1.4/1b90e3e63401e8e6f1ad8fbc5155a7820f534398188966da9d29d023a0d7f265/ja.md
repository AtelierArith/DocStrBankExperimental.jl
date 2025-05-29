```
setmin!(model::AbstractModel, min::Union{Number, AbstractVector})
setmin!(model::AbstractModel, i::Integer, min::Number)
```

`model`内の変数の下限を`min`に設定します。もし`i`が指定されている場合は、`model`内の`i`番目の変数の下限を`min`に設定します。
