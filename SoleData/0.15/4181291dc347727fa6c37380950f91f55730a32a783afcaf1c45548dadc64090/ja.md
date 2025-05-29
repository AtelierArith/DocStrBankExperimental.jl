```
parsecondition(C::Type{<:AbstractCondition}, expr::String; kwargs...)
```

タイプ `C` の条件をその [`syntaxstring`](@ref) 表現から解析します。`C` に応じて、`featuretype::Type{<:AbstractFeature}` や `featvaltype::Type` のようなキーワード引数を指定することが必要または推奨される場合があります。

他にも [`parsefeature`](@ref) を参照してください。
