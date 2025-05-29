```
mutable struct FixedRanks <: RankCheck
    r::Vector{Int}
    current::Int
end
```

`i`番目のランクは、特異値に関係なく`r[i]`にハードコーディングされています。フィールド`current`は、すでにいくつのランクが要求されたかを示します。`current`が`length(r)`のとき、これ以上ランクを要求することはできません。

## 例

```jldoctest
julia> check = FixedRanks([2, 3])
FixedRanks([2, 3], 0)

julia> rank_from_singular_values([1, 1e-1, 5e-5, 1e-5, 5e-6], check)
2

julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], check)
3
```
