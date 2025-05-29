```
ImpostorTemplate(formats::Union{T, S, Vector{Union{T, S}}}) where {T<:AbstractString, S<:Symbol}
```

新しいテーブルを生成するために使用される`formats`を格納する構造体。`formats`の各要素は、Impostorによってエクスポートされた生成関数にマッピングされます。この構造体は後で*ファンクタ*として使用され、データを生成するために、新しい`ImpostorTemplate`オブジェクトをインスタンス化した後、このオブジェクトが呼び出され、データエントリを生成するための引数が提供されます。

# パラメータ

  * `formats` (`String`, `Symbol` または `Vector{Union{String, Symbol}}`): 各列で使用される生成関数の観点から指定されたテーブル出力形式（以下の例を参照）。

# 例

```@repl
julia> imp = ImpostorTemplate("firstname")
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate(:firstname)
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate(["firstname"])
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate([:firstname])
ImpostorTemplate([:firstname])
```
