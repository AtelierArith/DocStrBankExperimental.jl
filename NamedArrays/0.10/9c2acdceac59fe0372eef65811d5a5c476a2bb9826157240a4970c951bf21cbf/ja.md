```
dimnames(n::NamedArray, [d::Integer])
```

NamedArray `n` の `d`'番目の次元の名前を返す。`d` が指定されていない場合は、すべての次元の名前を返す。

# 例

```jldoctest
julia> n = NamedArray([1 2; 3 4; 5 6], (["一", "二", "三"], ["first", "second"]), ("cmn", "en"))
3×2 Named Matrix{Int64}
cmn ╲ en │  first  second
─────────┼───────────────
一       │      1       2
二       │      3       4
三       │      5       6

julia> dimnames(n)
2-element Vector{String}:
"cmn"
"en"
```
