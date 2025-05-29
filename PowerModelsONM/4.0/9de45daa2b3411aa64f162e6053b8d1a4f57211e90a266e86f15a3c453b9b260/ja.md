```
correct_deprecated_properties!(orig_properties::T, new_properties::T, deprecated_properties::T)::Tuple{T,T} where T <: Dict{String,Any}
```

`orig_properties` において非推奨となったプロパティを `new_properties` に修正するためのヘルパー関数です。
