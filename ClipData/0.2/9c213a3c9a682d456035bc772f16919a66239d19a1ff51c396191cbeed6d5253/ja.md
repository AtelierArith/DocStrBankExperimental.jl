```
cliptable(; kwargs...)
```

クリップボードからテーブルを作成します。`CSV.File`を返し、その後`DataFrame`や他のTables.jl互換オブジェクトに変換できます。

`cliptable`は区切り文字を自動検出し、すべてのキーワード引数は直接`CSV.File`コンストラクタに渡されます。

## 例

```julia-repl
julia> # 文字列をクリップボードに送信
       """
       a, b
       1, 2
       100, 200
       """ |> clipboard

julia> cliptable()
2-element CSV.File{false}:
 CSV.Row: (a = 1,  b = 2)
 CSV.Row: (a = 100,  b = 200)
```
