```
build_ref(
    data::Dict{String,<:Any},
    ref_extensions::Vector{<:Function} = Vector{Function}([]))::Dict{Symbol,<:Any}
```

データ辞書からref辞書を構築します。さらに、ref辞書にはオプションの`ref_extensions`関数のベクターによって populatedされたフィールドを含めることができます。
