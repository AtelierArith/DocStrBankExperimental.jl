```
parse_inverters(
    inverter_file::String;
    validate::Bool=true
)::Dict{String,Any}
```

インバータのJSONファイルを解析します。 [`run_stability_analysis!`](@ref run_stability_analysis!) で使用されます。

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の [Inverters Schema](@ref Inverters-Schema) に対して検証されます。
