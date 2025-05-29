```julia
longestcommonsubstring(args; lengthonly)

```

複数の文字列/ベクトルの中で、最長の共通の非空の部分文字列/部分ベクトルを見つけます。

同じ長さのものが複数ある場合、すべての異なる答えが非決定的な順序で返されます。

```jldoctest
julia> longestcommonsubstring("ababab", "bababa", "abaabb")
1-element Vector{String}:
 "aba"
```

キーワード引数 `lengthonly` が `true` に設定されている場合、最長の共通部分文字列の長さのみが返されます。

```jldoctest
julia> longestcommonsubstring("ababab", "bababa", "abaabb"; lengthonly=true)
3
```
