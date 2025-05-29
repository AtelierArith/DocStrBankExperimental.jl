```
str_ends(string::String, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

文字列が特定のパターンで終わるかどうかを確認します。

引数

  * `string`: 入力文字列。
  * `pattern`: 確認するパターン。文字列または正規表現である可能性があります。
  * `negate`: 結果を否定するかどうか。デフォルトは `false` です。

戻り値 パターンで文字列が終わるかどうかを示すブール値のベクター。

例

```jldoctest
julia> str_ends("apple pineapple", r"^p")
false

julia> str_ends.(["apple", "banana", "pear", "pineapple"], r"e$")  # [true, false, false, true]
4-element BitVector:
 1
 0
 0
 1
julia> str_ends.(["apple", "banana", "pear", "pineapple"], r"e$", negate=true)  # [false, true, true, false]
4-element BitVector:
 0
 1
 1
 0
```
