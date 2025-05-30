```
parse_chemical(name, formula; kwargs...)
parse_chemical(::Type{<: Chemical}, name::AbstractString, formula::AbstractString; kwargs...)
```

化学名を解析し、化学オブジェクトを構築します。デフォルトのタイプは `Chemical` です。 `kwargs` は属性です。
