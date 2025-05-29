skipmissings(args...)

Return a tuple of iterators wrapping each of the iterators in `args`, but skipping elements at positions where at least one of the iterators returns `missing` (listwise deletion of missing values).

# Examples

```
julia> x = [1, 2, missing, 4]; y = [1, 2, 3, missing];

julia> tx, ty = skipmissings(x, y)
(Missings.SkipMissings{Array{Union{Missing, Int64},1},Tuple{Array{Union{Missing, Int64},1}}}
(Union{Missing, Int64}[1, 2, missing, 4], (Union{Missing, Int64}[1, 2, 3, missing],)), Missi
ngs.SkipMissings{Array{Union{Missing, Int64},1},Tuple{Array{Union{Missing, Int64},1}}}(Union
{Missing, Int64}[1, 2, 3, missing], (Union{Missing, Int64}[1, 2, missing, 4],)))

julia> collect(tx)
2-element Array{Int64,1}:
 1
 2

```
