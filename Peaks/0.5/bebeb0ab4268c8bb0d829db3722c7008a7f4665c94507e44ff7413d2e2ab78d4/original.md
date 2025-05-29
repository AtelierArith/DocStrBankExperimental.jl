```
peakheights!(indices, heights; [min, max]) -> (indices, heights)
peakheights!(pks::NamedTuple; [min, max]) -> NamedTuple
```

Filter (mutate) and return `indices` and `heights` by removing peaks that are less than `min` and/or greater than `max`.

If a NamedTuple `pks` is given, a new NamedTuple is returned with the same fields (references) from `pks`. `pks` must have `:indices` and `:heights` fields. The fields `:proms`, `:widths`, and `:edges` will be filtered (mutated) if present, and any remaining fields will be referenced unmodified.

See also: [`peakproms`](@ref), [`peakwidths`](@ref), [`findmaxima`](@ref) [`filterpeaks!`](@ref)

# Examples

```jldoctest
julia> x = [0,5,2,3,3,1,4,0];

julia> pks = findmaxima(x)
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> peakheights!(pks; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> inds, heights = peakheights!(pks.indices, pks.heights; min=3.5)
([7], [4])
```
