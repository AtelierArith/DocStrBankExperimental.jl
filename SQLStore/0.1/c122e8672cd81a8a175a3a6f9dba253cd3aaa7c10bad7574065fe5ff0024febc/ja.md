`create_table(db, name, T::Type{NamedTuple}; [constraints], [keep_compatible=false])`

データベース `db` に `name` という名前のテーブルを作成し、型 `T` から派生した列仕様を持ちます。テーブル制約は `constraints` 引数で指定できます。同じ `name` のテーブルがすでに存在する場合はエラーをスローしますが、`keep_compatible` が渡された場合は除外されます。`keep_compatible=true` の場合、互換性のあるスキーマを持つ既存のテーブルが保持されます。

サポートされている型:

  * `Int`、`Float64`、`String` はそれぞれ対応する SQL 型として直接保存されます。
  * `Bool` は `0` と `1` の `INTEGER` として保存されます。
  * `DateTime` は `'%Y-%m-%d %H:%M:%f'` 形式の `TEXT` として保存されます。
  * `Dict` と `Vector` はそれぞれの `JSON` 表現に変換されます。
  * 任意の型は `Union{Int, Missing}` のように `Missing` と組み合わせることができます。これにより、対応する列に `NULL` を含めることができます。
