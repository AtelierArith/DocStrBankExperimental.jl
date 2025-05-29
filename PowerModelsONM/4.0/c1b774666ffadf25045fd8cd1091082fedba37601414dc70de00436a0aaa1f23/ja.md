```
get_deprecated_properties(schema::T; deprecated_properties::Union{T,Missing}=missing)::T where T <: Dict{String,Any}
```

スキーマを通じて非推奨のプロパティを発見するための再帰関数
