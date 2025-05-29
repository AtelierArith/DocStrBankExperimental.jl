```
exec(ctx, "database", "engine", "query source"; kwargs...)
```

提供されたクエリ文字列を指定されたデータベースで同期的に実行します。この関数は、指定されたエンジンを使用してトランザクションを作成し、トランザクションが完了するまでポーリングし、トランザクションリソースとその結果およびメタデータを保持するDictを返します。

## キーワード引数:

  * `readonly = false`: trueの場合、これは「読み取り専用クエリ」であり、このトランザクションの影響はデータベースにコミットされません。
  * `inputs`: 関係名を値にマッピングする入力ペアのオプション辞書です。 （非推奨 - inputs Dictの形式は今後のリリースで変更されます。）

# 例:

```julia
julia> exec(ctx, "my_database", "my_engine", "def output {2 + 2}")
Dict{String, Any} with 4 entries:
  "metadata"    => Union{}[]
  "problems"    => Union{}[]
  "results"     => Pair{String, Arrow.Table}["/:output/Int64"=>Arrow.Table with 1 r…
  "transaction" => {…

julia> exec(ctx, "my_database", "my_engine", """
           def insert[:my_relation]: (1, 2, 3)
           """,
           readonly = false,
       )
Dict{String, Any} with 4 entries:
  "metadata"    => Union{}[]
  "problems"    => Union{}[]
  "results"     => Any[]
  "transaction" => {…
```
