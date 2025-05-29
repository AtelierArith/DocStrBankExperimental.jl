```
parse_events!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    apply::Bool=true
)::Dict{String,Any}
```

[`parse_events`](@ref parse_events)を使用して、[`entrypoint`](@ref entrypoint)内で使用するために、イベントファイルをインプレースで解析します。

`apply`がtrueの場合、イベントをマルチネットワークデータ構造に適用します。

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の[Events Schema](@ref Events-Schema)に対して検証されます。
