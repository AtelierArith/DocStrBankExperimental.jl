`deleteonly!(query, tbl::Table)`

`query` に一致する唯一の行を `tbl` テーブルから削除します。`query` に一致する行がゼロまたは複数ある場合は例外をスローします。

フィルタリング `query` は SQL の `WHERE` 句に対応します。次のいずれかの形式で指定できます：

  * `NamedTuple`: 指定されたフィールドが対応するテーブルの列と一致し、`AND` で結合されます。値は対応する SQL 型に変換されます。詳細は `create_table` を参照してください。
  * `String`: そのまま保持されます。
  * タプル `(String, args...)`: `String` はそのまま `WHERE` に渡され、`args` は SQL ステートメントのパラメータで、`?` として参照できます。
  * タプル `(String, NamedTuple)`: `String` はそのまま `WHERE` に渡され、`NamedTuple` には名前で参照できる SQL ステートメントのパラメータが含まれています。`:param_name`。
