```
str_remove_all(string::String, pattern::Union{String, Regex})
```

文字列からパターンのすべての出現を削除します。

# 引数

  * `string`: パターンを削除する対象の文字列。
  * `pattern`: 文字列から削除されるべきパターン。文字列または正規表現である可能性があります。

すべての出現が削除された文字列を返します。

例

```jldoctest
julia> string = "I love tidier strings, I love tidier strings"
"I love tidier strings, I love tidier strings"

julia> str_remove_all(string, " strings")
"I love tidier , I love tidier "
```
