```
setmax!(model::AbstractModel, max::Union{Number, AbstractVector})
setmax!(model::AbstractModel, i::Integer, max::Number)
```

`model`内の変数の上限を`max`に設定します。もし`i`が指定されている場合は、`model`内の`i`番目の変数の上限を`max`に設定します。
