```
simple_table(table, [columns];
    halign = :center,
    subheaders = nothing,
    table_kwargs...
)
```

生の列の（サブセット）を表示するシンプルな `Table` を作成します。

## 引数

  * `table`: Tables.jl 互換のデータソース
  * `columns`: テーブルから選択する列名のベクターで、オプションの表示名が付けられています。列名は `Symbol` または `String` のいずれかであることができます。異なる表示名は、表示名が SummaryTables がレンダリングできる任意のオブジェクトである `Pair` 構文を使用して渡すことができます。例えば `[:a, :b => "B", "c"]` のように。

## キーワード引数

  * `halign = :center`: `:left`、`:right`、`:center` のいずれか、または表示する列の数と同じ数のこれらの値のベクター。
  * `subheaders = nothing`: サブヘッダーを表示するには、表示する列の数と同じ数の、SummaryTables がレンダリングできるオブジェクトのベクターを渡します。
