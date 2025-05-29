```
subtract_overscan(frame, idxs; dims = axes_min_length(idxs), [hdu = 1])
```

Subtract the overscan frame from image.

`dims` is the dimension along which `overscan_frame` is combined. The default value of `dims` is the axis with smaller length in overscan region. If `idxs` is a string it will be parsed as FITS-style indices.

If `frame` is a string, it will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` which by default is 1.

# Examples

```jldoctest
julia> frame = [4.0 2.0 3.0 1.0 1.0];

julia> subtract_overscan(frame, (:, 4:5), dims = 2)
1×5 Matrix{Float64}:
 3.0  1.0  2.0  0.0  0.0

julia> subtract_overscan(frame, "[4:5, 1:1]", dims = 2)
1×5 Matrix{Float64}:
 3.0  1.0  2.0  0.0  0.0
```

# See Also

[`subtract_overscan!`](@ref)
