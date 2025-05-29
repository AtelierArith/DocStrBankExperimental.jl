```
parse_vue_html(html, level = 0; indent::Union{String, Int} = 4, vec_sep::String = ",
```

", context = @**MODULE**)

HTMLコードをJulia/StippleUIコードに自動的な改行とインデントを伴って解析します。インデントは以下によって決定されます。

  * `level`: フォーマットの開始レベル; 負の値も許可され、負のレベルはインデントされません
  * `indent`: 各レベルあたりの' '文字数の整数または文字列値
  * `vec_sep`: 配列リストの区切り文字、妥当な値は`",\n"`, `"\n\n"`, `",\n\n"`です
  * `context`: 評価のためのコンテキスト

```
