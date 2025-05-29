```
parse_events(
    events_file::String;
    validate::Bool=true
)::Vector{Dict{String,Any}}
```

イベントファイルを生のイベントデータ構造に解析します

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の[Events Schema](@ref Events-Schema)に対して検証されます。
