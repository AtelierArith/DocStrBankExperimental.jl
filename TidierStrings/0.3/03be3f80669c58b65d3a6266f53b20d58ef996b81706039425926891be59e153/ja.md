```
str_locate_all(string::AbstractString, pattern::Union{AbstractString, Regex})
```

文字列内のパターンのすべての出現位置のインデックスを返します。

引数

  * `string`: 入力文字列。
  * `pattern`: 検索するパターン。文字列または正規表現である可能性があります。

マッチの開始位置を示す `start` と終了位置を示す `end` のタプル `(start, end)` のベクトル。

例

```jldoctest
julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate_all(fruit[1], "e")
1-element Vector{Tuple{Int64, Int64}}:
 (5, 5)

julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate_all(fruit[2], "a")
3-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (4, 4)
 (6, 6)
```
