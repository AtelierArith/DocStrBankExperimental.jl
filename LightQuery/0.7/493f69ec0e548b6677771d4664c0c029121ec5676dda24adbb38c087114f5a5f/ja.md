```
RightJoin(left::By, right::By)
```

`isequal(left.key_function(left.sorted), right.key_function(right.sorted))` が成り立つすべてのペアを見つけ、左側の一致がない場合は `missing` を使用します。`left` と `right` はどちらも厳密にソートされていると仮定します（重複なし）。重複がある場合は、最初に [`Group`](@ref) を使用してください。詳細は [`By`](@ref) を参照してください。

```jldoctest
julia> using LightQuery


julia> collect(RightJoin(By([1, -2, 5, -6], abs), By([-1, 3, -4, 6], abs)))
4-element Array{Tuple{Union{Missing, Int64},Int64},1}:
 (1, -1)
 (missing, 3)
 (missing, -4)
 (-6, 6)

julia> collect(RightJoin(By(Int[], abs), By(Int[], abs))) == []
true

julia> collect(RightJoin(By([1], abs), By(Int[], abs))) == []
true

julia> collect(RightJoin(By(Int[], abs), By([1], abs)))
1-element Array{Tuple{Union{Missing, Int64},Int64},1}:
 (missing, 1)
```
