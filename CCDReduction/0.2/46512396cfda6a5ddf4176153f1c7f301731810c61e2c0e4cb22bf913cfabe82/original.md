```
crop(frame, shape; force_equal = true, [hdu = 1])
```

Crops `frame` to the size specified by `shape` anchored by the frame center.

This will remove rows/cols of the `frame` equally on each side. When there is an uneven difference in sizes (e.g. size 9 -> 6 can't be removed equally) the default is to increase the output size (e.g. 6 -> 7) so there is equal removal on each side. To disable this, set `force_equal=false`, which will remove the extra slice from the end of the axis.

If `frame` is a string, it will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` which by default is 1.

# Examples

```jldoctest
julia> frame = reshape(1:25, (5, 5));

julia> crop(frame, (3, 3))
3×3 Matrix{Int64}:
 7  12  17
 8  13  18
 9  14  19

julia> crop(frame, (4, 3), force_equal = false)
4×3 Matrix{Int64}:
 6  11  16
 7  12  17
 8  13  18
 9  14  19
```

# See Also

[`cropview`](@ref)
