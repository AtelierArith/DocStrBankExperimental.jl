```
str_which(string::Vector{T}, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

パターンに対して少なくとも1つの一致がある文字列のインデックスを返します。

# 引数

  * `string`: 入力文字列。
  * `pattern`: チェックするパターン。文字列または正規表現である可能性があります。
  * `negate`: 結果を否定するかどうか。デフォルトは `false` です。

# 返り値

一致する文字列のインデックスを含む整数ベクトル。

# 例

```jldoctest
julia> str_which(["apple", "banana", "pear", "pineapple"], r"a")  # [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4
julia> str_which(["apple", "banana", "pear", "pineapple"], r"a", negate=true)  # []
Int64[]
julia> str_which(["apple", "banana", "pear", "pineapple"], "a", negate=true)  # []
Int64[]
```
