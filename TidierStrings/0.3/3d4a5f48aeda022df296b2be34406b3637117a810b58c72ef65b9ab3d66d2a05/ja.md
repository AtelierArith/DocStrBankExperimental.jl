```
str_dup(s::AbstractString, times::Int)
```

文字列 `s` を `times` 回複製します。

引数

  * `s`: 入力文字列。
  * `times`: 文字列を複製する回数。

戻り値 文字列 `s` が `times` 回複製された文字列。

例

```jldoctest
julia> str_dup("hello", 3)
"hellohellohello"
```
