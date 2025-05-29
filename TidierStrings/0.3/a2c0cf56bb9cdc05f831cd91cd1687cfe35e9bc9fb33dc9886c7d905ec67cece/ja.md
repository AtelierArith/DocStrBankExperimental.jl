```
str_trim(s::AbstractString, side::String="both")
```

文字列 `s` の左側と右側、または `side` が "both" の場合は両側からすべての空白を削除します。

引数

  * `s`: 入力文字列。
  * `side`: 空白を削除する側。 "left"、"right"、または "both" のいずれか。

戻り値 `s` の左側と右側、または `side` が "both" の場合は両側からすべての空白が削除された文字列。

例

```jldoctest
julia> str_trim("  hello world! 😊  ")
"hello world! 😊"
```
