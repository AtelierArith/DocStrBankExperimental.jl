```
names(n::NamedArray, [d::Integer])
```

次元 `d` に沿ったインデックスの名前を抽出します。`d` が指定されていない場合は、すべての次元の名前を抽出します。

# 例

```jldoctest
julia> n = NamedArray([1, 2, 3], (["one", "二", "trois"],))
3-element Named Vector{Int64}
A     │ 
──────┼──
one   │ 1
二    │ 2
trois │ 3

julia> names(n)
1-element Vector{Vector{String}}:
    ["one", "二", "trois"]
```
