```
test_vue_parsing(html_string; prettify::Bool = true, level = 0, indent = 4, context = @__MODULE__)
```

HTMLコードを自動的な改行とインデントを用いてJulia/StippleUIコードに解析し、コードを実行して結果を整形します。インデントは以下によって決定されます。

  * `level`: フォーマットの開始レベル; 負の値も許可され、負のレベルはインデントされません
  * `indent`: レベルごとの' '文字数の整数または文字列値
  * `context`: 評価のためのコンテキスト
