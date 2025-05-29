```
parse_settings(
    settings_file::String;
    validate::Bool=true
    correct::Bool=true
)::Dict{String,Any}
```

ネットワーク設定のJSONファイルを解析します。

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の[Settings Schema](@ref Settings-Schema)に対して検証されます。
