```
flat_correct(frame, flat_frame; norm_value = mean(flat_frame), [hdu = 1])
```

Correct `frame` for non-uniformity using the calibrated `flat_frame`.

By default, the `flat_frame` is normalized by its mean, but this can be changed by providing a custom `norm_value`.

If either are strings, they will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` as either an integer or a tuple corresponding to each file.

!!! note
    This function may introduce non-finite values if `flat_frame` contains values very close to `0` due to dividing by zero. The default behavior will return `Inf` if the frame value is non-zero, and `Nan` if the frame value is `0`.


# Examples

```jldoctest
julia> frame = ones(3, 3);

julia> flat = fill(2.0, (3, 3));

julia> flat_correct(frame, flat, norm_value = 1.0)
3×3 Matrix{Float64}:
 0.5  0.5  0.5
 0.5  0.5  0.5
 0.5  0.5  0.5

julia> flat_correct(frame, flat)
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0
 1.0  1.0  1.0
```

# See Also

[`flat_correct!`](@ref)
