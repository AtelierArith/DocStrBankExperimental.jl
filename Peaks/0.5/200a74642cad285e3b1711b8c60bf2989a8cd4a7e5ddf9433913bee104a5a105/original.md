```
peakheights(indices, heights; [min, max]) -> (indices, heights)
peakheights(pks::NamedTuple; [min, max]) -> NamedTuple
```

Return a copy of `indices` and `heights` where peaks are removed if their height is less than `min` and/or greater than `max`.

If a NamedTuple `pks` is given, a new NamedTuple is returned with filtered copies of fields from `pks`. `pks` must have `:indices` and `:heights` fields. The fields `:proms`, `:widths`, and `:edges` will be filtered if present, and any remaining fields will be copied unmodified.

See also: [`peakproms`](@ref), [`peakwidths`](@ref), [`findmaxima`](@ref)

# Examples

```jldoctest
julia> x = [0,5,2,3,3,1,4,0];

julia> pks = findmaxima(x)
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> peakheights(pks; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> inds, heights = peakheights(pks.indices, pks.heights; max=4)
([4, 7], [3, 4])
```
