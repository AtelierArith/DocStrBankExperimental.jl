```
str_replace(string::String, pattern::Union{String, Regex}, replacement::String)
```

文字列内のパターンの最初の出現を指定された文字列で置き換えます。

引数 string: パターンを置き換える文字列。 pattern: 文字列内で見つけるための文字列または正規表現。 replacement: パターンの代わりに挿入する文字列。 パターンには特別なロジックを含めることができます：

| を使用して「または」を表します（例: "red|blue" は "red" または "blue" を含む任意の文字列に一致します）。 戻り値 新しい文字列で、パターンの最初の出現が置き換えられたもの。 例

```jldoctest
julia> str_replace("I Think You Should Leave is a great show", " ", "")
"IThink You Should Leave is a great show"

julia> str_replace("The sky is blue", "blue", "red")
"The sky is red"

julia> str_replace("The sky is blue", r"blu", "red")
"The sky is blue"

julia> str_replace("The sky is blue", "blue|sky", "red")
"The red is blue"
```
