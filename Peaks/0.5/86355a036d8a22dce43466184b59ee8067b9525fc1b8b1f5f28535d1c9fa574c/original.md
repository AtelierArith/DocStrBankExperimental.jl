```
peakwidths(indices, x, proms; [strict=true, relheight=0.5, min, max]) -> (indices, widths, ledge, redge)
peakwidths(pks::NamedTuple; [strict=true, relheight=0.5, min, max]) -> NamedTuple
```

Calculate the widths of peak `indices` in `x` at a reference level based on `proms` and `relheight`, and removing peaks with widths less than `min` and/or greater than `max`. Returns the peaks, widths, and the left and right edges at the reference level.

Peak width is the distance between the signal crossing a reference level before and after the peak. Signal crossings are linearly interpolated between indices. The reference level is the difference between the peak height and `relheight` times the peak prominence. Width cannot be calculated for a `NaN` or `missing` prominence.

If a NamedTuple `pks` is given, a new NamedTuple is returned with filtered copies of fields from `pks`. `pks` must have `:indices`, `:heights`, and `:proms` fields. If `pks` has `:widths` and `:edges` fields, they will not be recalculated, but filtered only. Any remaining fields will be copied unmodified.

If `strict == true`, the width for a peak with a gap in the signal (e.g. `NaN`, `missing`) at the reference level will match the gap (e.g. `NaN` for `NaN`, etc.). Otherwise, the signal crossing will be linearly interpolated between the edges of the gap.

See also: [`peakwidths!`](@ref), [`peakproms`](@ref), [`findmaxima`](@ref)

# Examples

```jldoctest
julia> x = Float64[0,5,2,2,3,3,1,4,0];

julia> pks = findmaxima(x) |> peakproms!(;max=2);

julia> peakwidths(pks)
(indices = [5], heights = [3.0], data = [0.0, 5.0, 2.0, 2.0, 3.0, 3.0, 1.0, 4.0, 0.0], proms = [1.0], widths = [1.75], edges = [(4.5, 6.25)])

julia> x[4] = NaN;

julia> peakwidths(pks.indices, x, pks.proms)
([5], [NaN], [NaN], [6.25])

julia> peakwidths(pks.indices, x, pks.proms; strict=false)
([5], [2.25], [4.0], [6.25])
```
