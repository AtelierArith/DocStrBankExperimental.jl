```
str_unique(strings::AbstractVector{<:AbstractString}; ignore_case::Bool=false)
```

文字列のベクターから重複を削除します。

引数

  * `strings`: 入力文字列のベクター。
  * `ignore_case`: 文字列を比較する際に大文字と小文字を無視するかどうか。デフォルトは `false` です。

戻り値 入力ベクターからのユニークな文字列のベクター。

例

```jldoctest
julia> str_unique(["apple", "banana", "pear", "banana", "Apple"])
4-element Vector{String}:
 "apple"
 "banana"
 "pear"
 "Apple"
```
