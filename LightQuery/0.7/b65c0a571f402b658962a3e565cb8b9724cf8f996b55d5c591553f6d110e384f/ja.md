```
InnerJoin(left::By, right::By)
```

`isequal(left.key_function(left.sorted), right.key_function(right.sorted))` が成り立つすべてのペアを見つけます。`left` と `right` はどちらも厳密にソートされていると仮定します（重複なし）。重複がある場合は、最初に [`Group`](@ref) を使用してください。詳細は [`By`](@ref) を参照してください。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred collect(InnerJoin(By([1, -2, 5, -6], abs), By([-1, 3, -4, 6], abs)))
2-element Array{Tuple{Int64,Int64},1}:
 (1, -1)
 (-6, 6)

julia> (@inferred collect(InnerJoin(By(Int[], abs), By(Int[], abs)))) == []
true

julia> (@inferred collect(InnerJoin(By([1], abs), By(Int[], abs)))) == []
true

julia> (@inferred collect(InnerJoin(By(Int[], abs), By([1], abs)))) == []
true
```
