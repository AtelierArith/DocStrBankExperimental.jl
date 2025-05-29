str*extract*all(strings, pattern::Union{String, Regex}; captures::Bool)

文字列からパターンのすべての出現を抽出します

# 引数

  * `strings`: 一致を検索する文字列。
  * `pattern`: 検索するパターン、StringまたはRegexとして。
  * `captures`: trueの場合、一致の代わりにキャプチャグループを返します。

# 例

```jldoctest julia> str*extract*all("hello world hello universe hello goodbye", r"hello") 3-element Vector{String}:  "hello"  "hello"  "hello"

```
