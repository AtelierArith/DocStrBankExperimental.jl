```
InnerJoin(left::By, right::By)
```

Find all pairs where `isequal(left.key_function(left.sorted), right.key_function(right.sorted))`. Assumes `left` and `right` are both strictly sorted (no repeats). If there are repeats, [`Group`](@ref) first. See [`By`](@ref).

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
