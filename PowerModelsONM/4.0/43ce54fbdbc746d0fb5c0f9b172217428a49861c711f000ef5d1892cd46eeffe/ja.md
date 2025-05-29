```
parse_events(
    events_file::String,
    mn_data::Dict{String,<:Any};
    validate::Bool=true
)::Dict{String,Any}
```

`events_file`から生のイベントを解析し、それを[`parse_events`](@ref parse_events)に渡してネイティブデータ型に変換します。

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の[Events Schema](@ref Events-Schema)に対して検証されます。
