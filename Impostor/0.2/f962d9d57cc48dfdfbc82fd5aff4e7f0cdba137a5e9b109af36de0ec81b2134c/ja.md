```
render_alphanumeric(template::AbstractString; numbers, letters) :: String
```

アルファベットと数字のテンプレート文字列（例: `"^^^-####"`）を受け取り、次のように置き換えた文字列を生成します：

  * `'#'` 文字を [0, 9] の間のランダムな数字で置き換えます。
  * `'^'` 文字を A-Z の間のランダムな大文字のアルファベットで置き換えます。
  * `'_'` 文字を a-z の間のランダムな小文字のアルファベットで置き換えます。
  * `'='` 文字を a-z|A-Z の間のランダムな大文字または小文字のアルファベットで置き換えます。

オプションで、`template` の `'#'` プレースホルダーを埋めるための `numbers` を提供するか、`'^'`、`'_'` または `'='` プレースホルダーを埋めるための `letters` を提供します。`letters` または `numbers` の長さが各カテゴリのプレースホルダーの数よりも小さい場合、残りのプレースホルダーは `template` の文字に従ってランダムに埋められます。

# 例

```@repl
julia> render_alphanumeric("####")
"6273"

julia> render_alphanumeric("123-####-AAA")
"123-5509-AAA"

julia> render_alphanumeric("__-^^-==-ZZZ123")
"vw-CX-fA-ZZZ123"

julia> render_alphanumeric("__-^^-==-ZZZ###"; numbers = "12345")
"qu-RT-St-ZZZ123"

julia> render_alphanumeric("__-^^-==-ZZZ###"; letters = "AABBCCDD")
"AA-BB-CC-ZZZ427"

julia> render_alphanumeric("__-^^-==-ZZZ###"; letters = "AABBCCDD", numbers = "12345")
"AA-BB-CC-ZZZ123"

julia> render_alphanumeric("_______"; letters = "abc")
"abcomhd"
```
