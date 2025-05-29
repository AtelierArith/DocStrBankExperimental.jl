```
filterpeaks!(pks::NT, feature; [min, max]) where {NT<:NamedTuple} -> pks::NT
filterpeaks!(pks::NT, mask) -> pks::NT
```

Filter the standard `pks` fields where peaks are removed if `pks.$feature` is less than `min` and/or greater than `max`. If a `mask` is given, a given peak `i` is filtered (removed) if `mask[i]` is `false`.

Standard Peaks.jl fields of `pks` are `:indices`, `:proms`, `:heights`, `:widths`, `:edges`.

# Examples

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0])
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> filterpeaks!(pks, :heights; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> pks = findmaxima([0,5,2,3,3,1,4,0]) |> peakproms!();

julia> mask = [pks.heights[i] < 5 &&  pks.proms[i] > 2 for i in eachindex(pks.indices)]
3-element Vector{Bool}:
 0
 0
 1

julia> filterpeaks!(pks, mask)
(indices = [7], heights = [4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[3])
```
