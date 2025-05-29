```julia
SimpleCellFormatter(; inf, minus_inf, NaN, nothing, missing)

```

データを表示する際に使用される一般的な値を置き換えるシンプルなフォーマッタです。

以下の各フィールドには、文字列または `LaTeX` コードを含める必要があります（そうでない場合は、エスケープされた文字列として出力されます）。
