```
subtract_dark(frame, dark_frame; data_exposure = 1, dark_exposure = 1, [hdu = 1])
```

Subtract the `dark_frame` from `frame`.

If either are strings, they will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` as either an integer or a tuple corresponding to each file.

# Examples

```jldoctest
julia> frame = ones(3, 3);

julia> dark_frame = ones(3, 3);

julia> subtract_dark(frame, dark_frame)
3×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> subtract_dark(frame, dark_frame, data_exposure = 1, dark_exposure = 4)
3×3 Matrix{Float64}:
 0.75  0.75  0.75
 0.75  0.75  0.75
 0.75  0.75  0.75

```

# See Also

[`subtract_dark!`](@ref)
