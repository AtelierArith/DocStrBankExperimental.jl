```
setnames!(n::NamedArray, v::Vector{T}, d::Integer)
```

`n`の次元`d`に沿った名前を`v`に設定します。  

NamedArray `n`はすでに型`T`の名前を持っている必要があります。

# 例

```jldoctest
julia> n = NamedArray([1 2; 3 4; 5 6])
3×2 Named Matrix{Int64}
A ╲ B │ 1  2
──────┼─────
1     │ 1  2
2     │ 3  4
3     │ 5  6

julia> setnames!(n, ["一", "二", "三"], 1)
(OrderedCollections.OrderedDict{Any, Int64}("一" => 1, "二" => 2, "三" => 3), OrderedCollections.OrderedDict{Any, Int64}("1" => 1, "2" => 2))
```
