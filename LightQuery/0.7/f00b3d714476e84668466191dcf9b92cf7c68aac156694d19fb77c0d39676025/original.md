```
LeftJoin(left::By, right::By)
```

Find all pairs where `isequal(left.key_function(left.sorted), right.key_function(right.sorted))`, using `missing` when there is no right match. Assumes `left` and `right` are both strictly sorted (no repeats). If there are repeats, [`Group`](@ref) first. See [`By`](@ref).

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
