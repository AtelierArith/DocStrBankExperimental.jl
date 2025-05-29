```
get_row_idxs(table, conditions) -> row_idxs
```

渡されたテーブルの行インデックスを返します。`conditions`は次のように指定できます。

  * `::Colon` - すべての行
  * `::Int64` - 単一の行
  * `::AbstractVector{Int64}` - 行のリスト
  * `p::Pair` - `comparison(p[2], typeof(row[p[1]]))(row[p[1]])`が真である各行のインデックスを含むベクターを返します。 [`comparison`](@ref)を参照してください。
  * `pairs`、`Pair`のイテレータ - 上記のようにすべてのペアを満たすインデックスを含むベクターを返します。

フィルタリングに使用できるペアの例：

  * `:nation => "narnia"`: `nation`列が文字列"narnia"と等しいかどうかをチェックします。
  * `:emis_co2 => >=(0.1)`: `emis_co2`列が0.1以上であるかどうかをチェックします。
  * `:age => (2,10)`: `age`列が2から10の間（両端を含む）であるかどうかをチェックします。排他的にするには、明確さのために(2.0001, 9.99999)のような異なる値を使用してください。
  * `:state => in(("alabama", "arkansas"))`: `state`列が"alabama"または"arkansas"のいずれかであるかどうかをチェックします。

[`get_table`](@ref)および[`get_table_row_idxs`](@ref)で使用されます。
