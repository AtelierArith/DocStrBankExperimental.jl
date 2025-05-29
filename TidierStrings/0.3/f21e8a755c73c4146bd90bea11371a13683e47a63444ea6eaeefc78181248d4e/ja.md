```
str_starts(string::String, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

特定のパターンで文字列が始まるかどうかを確認します。

引数

  * `string`: 入力文字列。
  * `pattern`: 確認するパターン。文字列または正規表現である可能性があります。
  * `negate`: 結果を否定するかどうか。デフォルトは `false` です。

戻り値 パターンで文字列が始まるかどうかを示すブール値のベクター。

例

```jldoctest
julia> str_starts.(["apple", "banana", "pear", "pineapple"], r"^p")  # [false, false, true, true]
4-element BitVector:
 0
 0
 1
 1
julia> str_starts.(["apple", "banana", "pear", "pineapple"], r"^p", negate=true)  # [true, true, false, false]
4-element BitVector:
 1
 1
 0
 0
julia> str_starts("apple pineapple", r"^p")
false
```
