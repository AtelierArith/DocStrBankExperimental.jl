```
trim(frame, idxs; [hdu = 1])
```

Trims the `frame` to remove the region specified by idxs.

This function trims the array in a manner such that final array should be rectangular. The indices follow standard Julia convention, so `(:, 45:60)` trims all columns from 45 to 60 and `(1:20, :)` trims all the rows from 1 to 20. The function also supports FITS-style indices.

If `frame` is a string, it will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` which by default is 1.

# Examples

```jldoctest
julia> frame = ones(5, 5);

julia> trim(frame, (:, 2:5))
5×1 Matrix{Float64}:
 1.0
 1.0
 1.0
 1.0
 1.0

julia> trim(frame, "[2:5, 1:5]")
5×1 Matrix{Float64}:
 1.0
 1.0
 1.0
 1.0
 1.0

```

# See Also

[`trimview`](@ref)
