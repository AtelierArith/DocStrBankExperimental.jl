```
parse_settings!(
    args::Dict{String,<:Any};
    apply::Bool=true,
    validate::Bool=true
)::Dict{String,Any}
```

ランタイム引数で指定された設定ファイルをインプレースで解析します。

非推奨のランタイム引数を適切なネットワーク設定データ構造に変換しようとします。

## 検証

`validate=true`（デフォルト）の場合、解析されたデータ構造は最新の [Settings Schema](@ref Settings-Schema) に対して検証されます。
