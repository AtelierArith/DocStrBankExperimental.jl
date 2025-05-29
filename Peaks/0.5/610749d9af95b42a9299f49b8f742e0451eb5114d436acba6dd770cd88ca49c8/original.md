```
peakproms(indices, x; [strict=true, min, max]) -> (indices, proms)
peakproms(pks::NamedTuple; [strict=true, min, max]) -> NamedTuple
```

Calculate the prominences of peak `indices` in `x`, and remove peaks with prominences less than `min` and/or greater than `max`.

Peak prominence is the absolute height (value) difference between the current peak and the larger of the two adjacent smallest magnitude points between the current peak and adjacent larger peaks or signal ends.

If a NamedTuple `pks` is given, a new NamedTuple is returned with filtered copies of fields from `pks`. `pks` must have `:indices` and `:heights` fields. If `pks` has a `:proms` field, prominences will only be filtered, and not be recalculated. The fields `:widths` and `:edges` will also be filtered if present, and any remaining fields will be copied unmodified.

If `strict == true`, the prominence for a peak with a `NaN` or `missing` between the current peak and either adjacent larger peaks will be `NaN` or `missing`, otherwise, it will be the larger of the smallest non-`NaN` or `missing` values between the current peak and adjacent larger peaks for `strict == false`.

See also: [`peakproms!`](@ref), [`findmaxima`](@ref)

# Examples

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0]);

julia> pks = peakproms(pks; min=2)
(indices = [2, 7], heights = [5, 4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[5, 3])

julia> inds, proms = peakproms(pks.indices, pks.data; max=4)
([7], Union{Missing, Int64}[3])
```
