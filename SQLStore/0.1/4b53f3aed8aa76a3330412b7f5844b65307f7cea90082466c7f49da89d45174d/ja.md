`update!(query => qset, tbl::Table)`

`query` に一致する行を `qset` 仕様で更新します。

フィルタリング `query` は SQL の `WHERE` 句に対応します。以下のいずれかの形式で指定できます：

  * `NamedTuple`: 指定されたフィールドは対応するテーブルの列と一致し、`AND` で結合されます。値は対応する SQL 型に変換されます。詳細は `create_table` を参照してください。
  * `String`: そのまま保持されます。
  * タプル `(String, args...)`: `String` はそのまま `WHERE` に渡され、`args` は SQL ステートメントのパラメータで、`?` として参照できます。
  * タプル `(String, NamedTuple)`: `String` はそのまま `WHERE` に渡され、`NamedTuple` には名前で参照できる SQL ステートメントのパラメータが含まれています。`:param_name`。

`qset` 部分は `UPDATE` の SQL `SET` 句に対応します。以下の方法で指定できます：

  * `NamedTuple`: 指定されたフィールドはテーブルの列に対応します。値はその SQL 型に変換されます。詳細は `create_table` を参照してください。
  * `String`: そのまま保持されます。
  * タプル `(String, NamedTuple)`: `String` はそのまま `SET` に渡され、`NamedTuple` には名前で参照できる SQL ステートメントのパラメータが含まれています。`:param_name`。
