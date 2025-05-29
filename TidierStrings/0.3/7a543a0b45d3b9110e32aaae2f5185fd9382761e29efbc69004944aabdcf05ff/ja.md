```
str_locate(string::AbstractString, pattern::Union{AbstractString, Regex})
```

文字列内のパターンの最初の出現位置のインデックスを返します。

引数

  * `string`: 入力文字列。
  * `pattern`: 検索するパターン。文字列または正規表現である可能性があります。

タプル `(start, end)` で、`start` は一致の開始位置、`end` は終了位置です。

例

```jldoctest
julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate(fruit[1], "e")
(5, 5)

julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate(fruit[2], "a")
(2, 2)
```
