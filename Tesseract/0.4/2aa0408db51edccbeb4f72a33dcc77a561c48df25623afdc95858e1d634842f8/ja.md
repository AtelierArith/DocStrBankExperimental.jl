```
TessParam(
    name::AbstractString,
    value::AbstractString,
    help::AbstractString
)::TessParam{T} where T
```

提供された値から[`TessParam`](@ref)構造体の新しいインスタンスを構築します。

**引数:**

| T   | 名前    | デフォルト | 説明                   |
|:--- |:----- |:----- |:-------------------- |
| R   | name  |       | パラメータの名前/ID。         |
| R   | value |       | 文字列としてのパラメータのデフォルト値。 |
| R   | help  |       | パラメータに関するヘルプテキスト。    |

**詳細:**

このメソッドは`value`の内容を見て、作成する正しい[`TessParam`](@ref)タイプを決定します。

関連情報: [`tess_params_parsed`](@ref)
