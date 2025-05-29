```
summarytable(table, variable;
    rows = [],
    cols = [],
    summary = [],
    variable_header = true,
    celltable_kws...
)
```

`table` から `variable` 列の値を要約するサマリーテーブル `Table` を作成します。

## 引数

  * `table`: `DataFrames.DataFrame` に変換可能なデータソース。
  * `variable`: `table` から要約される変数を決定します。`:ColumnA` のような `Symbol` または `String` であるか、または `:ColumnA => "Column A"` のように表示名が第二要素である `Pair` であることができます。

## キーワード引数

  * `rows = []`: 行に沿ったグルーピング構造。各要素がグルーピング変数である `Vector` である必要があります。`Symbol` または `String` である `:Column1` のようなもの、または `:Column1 => "Column 1"` のように最初の要素がシンボルで第二の要素が表示名である `Pair` で指定します。複数のグルーピング変数を指定すると、ネストされたグループが作成され、最後の変数が最も早く変化します。
  * `cols = []`: 列に沿ったグルーピング構造。`rows` と同じ構造に従います。
  * `summary = []`: `variable` を要約するための関数を指定します。各エントリが1つの別々の要約である `Vector` である必要があります。各要約は `mean` や `maximum` のような `Function` として与えることができ、その場合表示名は関数の名前になります。あるいは、`mean => "Average"` のようにペア構文を使用して表示名を与えることもできます。デフォルトでは、すべてのグループに対して1つの要約が計算されます。また、`name => [...]` を渡すこともでき、ここで name は `Symbol` または `String` であるグルーピング列であり、そのグループの各レベルに対して1つの要約を計算します。
  * `variable_header = true`: 要約された `variable` の名前を持つセルが表示されるかどうかを制御します。
  * `sort = true`: グルーピングの前に入力テーブルをソートします。必要に応じて事前にソートし、特定のグループ順序を維持したい場合や、グループキーとしてソート不可能なオブジェクトを使用している場合は `false` に設定します。

その他のキーワードはすべて `Table` コンストラクタに転送されます。詳細についてはそのドキュメントを参照してください。

## 例

```
using Statistics

tbl = [
    :Apples => [1, 2, 3, 4, 5, 6, 7, 8],
    :Batch => [1, 1, 1, 1, 2, 2, 2, 2],
    :Delivery => ['a', 'a', 'b', 'b', 'a', 'a', 'b', 'b'],
]

summarytable(
    tbl,
    :Apples => "Number of apples",
    rows = [:Batch],
    cols = [:Delivery],
    summary = [length => "N", mean => "average", sum]
)
```
