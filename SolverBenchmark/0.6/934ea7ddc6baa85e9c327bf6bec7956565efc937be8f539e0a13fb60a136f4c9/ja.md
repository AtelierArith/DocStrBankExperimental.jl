```
pretty_latex_stats(df; kwargs...)
```

DataFrameをLaTeXのlongtableとしてPrettyTablesを使用して美しく表示します。

`pretty_stats`のドキュメントを参照してください。このメソッドの特定の設定は次のとおりです。

  * バックエンドは`:latex`に設定されています。
  * テーブルタイプは`:longtable`に設定されています。
  * ハイライターがある場合は、LaTeXハイライターである必要があります。

詳細については、PrettyTablesのドキュメントを参照してください。
