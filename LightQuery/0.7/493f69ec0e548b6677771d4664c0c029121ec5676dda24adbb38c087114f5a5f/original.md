```
RightJoin(left::By, right::By)
```

Find all pairs where `isequal(left.key_function(left.sorted), right.key_function(right.sorted))`, using `missing` when there is no left match. Assumes `left` and `right` are both strictly sorted (no repeats). If there are repeats, [`Group`](@ref) first. See [`By`](@ref).

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
