```
setnames!(n::NamedArray, v::Vector{T}, d::Integer)
```

Set the names of `n` along dimension `d` to `v`.  

The NamedArray `n` must already have names of type `T`

# Example

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
