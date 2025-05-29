```
LeftJoin(left::By, right::By)
```

`isequal(left.key_function(left.sorted), right.key_function(right.sorted))` が成り立つすべてのペアを見つけ、右側の一致がない場合は `missing` を使用します。`left` と `right` はどちらも厳密にソートされていると仮定します（重複なし）。重複がある場合は、最初に [`Group`](@ref) を使用してください。詳細は [`By`](@ref) を参照してください。

```jldoctest
julia> using LightQuery


julia> collect(LeftJoin(By([1, -2, 5, -6], abs), By([-1, 3, -4, 6], abs)))
4-element Array{Tuple{Int64,Union{Missing, Int64}},1}:
 (1, -1)
 (-2, missing)
 (5, missing)
 (-6, 6)

julia> collect(LeftJoin(By(Int[], abs), By(Int[], abs))) == []
true

julia> collect(LeftJoin(By([1], abs), By(Int[], abs)))
1-element Array{Tuple{Int64,Union{Missing, Int64}},1}:
 (1, missing)

julia> collect(LeftJoin(By(Int[], abs), By([1], abs))) == []
true
```
