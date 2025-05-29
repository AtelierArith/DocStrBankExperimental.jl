```
str_extract(string, pattern::Union{String, Regex})
```

文字列からパターンの最初の出現を抽出します

# 引数

  * `strings`: 一致を検索する文字列。
  * `pattern`: 検索するパターン。StringまたはRegexとして指定します。

# 例

```jldoctest julia> str_extract("hello world hello universe hello goodbye", r"hello") "hello"

julia> str_extract.(["hello world", "hello universe", "goodbye"], "hello") 3-element Vector{Union{Missing, String}}:  "hello"  "hello"  missing  ```
