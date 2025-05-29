```
listingtable(table, variable, [pagination];
    rows = [],
    cols = [],
    summarize_rows = [],
    summarize_cols = [],
    variable_header = true,
    table_kwargs...
)
```

`table` から生の値を表示する `variable` のリスティングテーブル `Table` を作成します。

## 引数

  * `table`: `DataFrames.DataFrame` に変換可能なデータソース。
  * `variable`: どの変数の生の値が表示されるかを決定します。`:ColumnA` のような `Symbol` または `String` であるか、または `:ColumnA => "Column A"` のように表示名が第二要素である `Pair` であることができます。
  * `pagination::Pagination`: ページネーションオブジェクトが渡されると、戻り値の型は `PaginatedTable` に変わります。`Pagination` オブジェクトは `rows` および/または `cols` のキーワードで作成できます。これらは、各側に含まれるグループセクションの数を決定する `Int` に設定する必要があります。これらのグループセクションは要約構造によって決定されます。なぜなら、ページネーションは一緒に要約されている行や列の中でリスティングテーブルを分割することは決してないからです。`summarize_rows` または `summarize_cols` が空または未設定の場合、その側の各グループはそれぞれ独自のセクションです。`summarize_rows` または `summarize_cols` に `column => ...` 構文を介してグループが渡されると、その側のグループセクションは `column` によって決定されます。そのような `column` が渡されない場合（すなわち、その側の要約がすべてのグループに適用される場合）、その側には1つのセクションしかなく、これはその側が1ページ以上にページネーションされることはできないことを意味します。

## キーワード引数

  * `rows = []`: 行に沿ったグループ構造。各要素がグループ変数である `Vector` である必要があります。これは `Symbol` または `String` であるか、`Pair` であり、最初の要素がシンボルで、第二の要素が表示名である必要があります（例: `:Column1 => "Column 1"`）。複数のグループ変数を指定すると、ネストされたグループが作成され、最後の変数が最も早く変化します。
  * `cols = []`: 列に沿ったグループ構造。`rows` と同じ構造に従います。
  * `summarize_rows = []`: 行に沿って `variable` を要約する関数を指定します。これは `Vector` であり、各エントリが1つの別々の要約です。各要約は `mean` や `maximum` のような `Function` として与えることができ、その場合、表示名は関数の名前になります。あるいは、`mean => "Average"` のようにペア構文を使用して表示名を与えることもできます。デフォルトでは、すべてのグループに対して1つの要約が計算されます。また、`name => [...]` を渡すこともでき、ここで `name` は `Symbol` または `String` であり、各レベルのそのグループに対して1つの要約を計算します。
  * `summarize_cols = []`: 列に沿って `variable` を要約する関数を指定します。`summarize_rows` と同じ構造に従います。
  * `variable_header = true`: 要約された `variable` の名前を持つセルが表示されるかどうかを制御します。
  * `sort = true`: グループ化の前に入力テーブルをソートします。必要に応じて事前にソートし、特定のグループ順序を維持したい場合や、グループキーとしてソート不可能なオブジェクトを使用している場合は `false` に設定します。

その他のすべてのキーワードは `Table` コンストラクタに転送されます。詳細についてはそのドキュメントを参照してください。

## 例

```
using Statistics

tbl = [
    :Apples => [1, 2, 3, 4, 5, 6, 7, 8],
    :Batch => [1, 1, 1, 1, 2, 2, 2, 2],
    :Checked => [true, false, true, false, true, false, true, false],
    :Delivery => ['a', 'a', 'b', 'b', 'a', 'a', 'b', 'b'],
]

listingtable(
    tbl,
    :Apples => "Number of apples",
    rows = [:Batch, :Checked => "Checked for spots"],
    cols = [:Delivery],
    summarize_cols = [sum => "total"],
    summarize_rows = :Batch => [mean => "average", sum]
)
```
