```
parsefeature(FT::Type{<:AbstractFeature}, expr::AbstractString; kwargs...)
```

型 `FT` の特徴をその [`syntaxstring`](@ref) 表現から解析します。`FT` に応じて、`featvaltype::Type` のようなキーワード引数を指定することが必要または推奨される場合があります。

他にも [`parsecondition`](@ref) を参照してください。
