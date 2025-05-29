```
peakwidths!(indices, x; [strict=true, relheight=0.5, min, max]) -> (indices, widths, ledge, redge)
peakwidths!(pks::NamedTuple; [strict=true, relheight=0.5, min, max]) -> NamedTuple
```

Calculate the widths of peak `indices` in `x` at a reference level based on `proms` and `relheight`, removing peaks with widths less than `min` and/or greater than `max`. Returns the modified peaks, widths, and the left and right edges at the reference level.

If a NamedTuple `pks` is given, a new NamedTuple is returned with the same fields (references) from `pks`. `pks` must have `:indices`, `:heights`, and `:proms` fields. If `pks` has `:widths` and `:edges` fields, they will not be recalculated, but filtered only. Any remaining fields will be copied unmodified.

See also: [`peakwidths`](@ref), [`peakproms`](@ref), [`findmaxima`](@ref)

# 

# Examples

```jldoctest ; filter = r"(\d*)\.(\d{3})\d*" => s"\1.\2***"
julia> x = Float64[0,5,2,2,3,3,1,4,0];

julia> pks = findmaxima(x) |> peakproms!();

julia> peakwidths!(pks; min=1)
(indices = [2, 5], heights = [5.0, 3.0], data = [0.0, 5.0, 2.0, 2.0, 3.0, 3.0, 1.0, 4.0, 0.0], proms = [5.0, 1.0], widths = [1.333, 1.75], edges = [(1.5, 2.833), (4.5, 6.25)])

julia> peakwidths!(pks.indices, pks.data, pks.proms; min=1)
([2, 5], [1.333, 1.75], [1.5, 4.5], [2.833, 6.25])
```
