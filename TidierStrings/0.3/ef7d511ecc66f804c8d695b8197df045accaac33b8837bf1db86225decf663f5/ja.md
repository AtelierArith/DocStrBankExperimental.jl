```
str_remove(string::String, pattern::Union{String, Regex})
```

文字列からパターンの最初の出現を削除します。

引数

  * `string`: パターンを削除する文字列。
  * `pattern`: 文字列から削除されるべきパターン。文字列または正規表現である可能性があります。

戻り値 パターンの最初の出現が削除された文字列。

例

```jldoctest
julia> string = "I love tidier strings strings"
"I love tidier strings strings"

julia> str_remove(string, " strings")
"I love tidier strings"
```
