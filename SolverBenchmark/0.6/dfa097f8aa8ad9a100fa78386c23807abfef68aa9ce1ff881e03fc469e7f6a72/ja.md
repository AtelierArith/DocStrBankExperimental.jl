```
pretty_stats(df; kwargs...)
```

PrettyTablesを使用してDataFrameをきれいに表示します。

### 引数

  * `io::IO`: テーブルが出力されるIOストリーム（デフォルト: `stdout`）;
  * `df::DataFrame`: 表示されるDataFrame。`df`の特定の列のみを表示する必要がある場合は、明示的に抽出する必要があります。例えば、`df[!, [:col1, :col2, :col3]]`を渡すことで行います。

### キーワード引数

  * `col_formatters::Dict{Symbol, String}`: 選択した`df`の列に適用するフォーマット文字列のDict。`col_formatters`のキーはシンボルである必要があり、特定の列に特定のフォーマットを適用できます。デフォルトでは、列の型に基づいて`default_formatters`が使用されます。`formatters`キーワード引数を使用してPrettyTablesフォーマッタを渡すと、`col_formatters`の前に適用されます。
  * `hdr_override::Dict{Symbol, String}`: 列名に従って単純に表示されるのではなく、異なる方法で表示されるべきヘッダーのDict（デフォルト: 空）。例: `Dict(:col1 => "column 1")`。

その他のすべてのキーワード引数は直接`pretty_table`に渡されます。特に、

  * Markdownテーブルを表示するには`tf=tf_markdown`を使用します;
  * LaTeX出力にはこの関数を使用しないでください; 代わりに`pretty_latex_stats`を使用してください;
  * すべてのPrettyTablesハイライターを指定できますが、事前定義された`passfail_highlighter`と`gradient_highlighter`を参照してください。
