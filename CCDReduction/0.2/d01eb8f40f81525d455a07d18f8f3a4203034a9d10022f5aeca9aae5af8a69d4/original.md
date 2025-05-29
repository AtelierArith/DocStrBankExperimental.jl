```
subtract_bias(frame, bias_frame; [hdu = 1])
```

Subtract the `bias_frame` from `frame`.

If either are strings, they will be loaded into [`CCDData`](@ref) first. The HDU loaded can be specified by `hdu` as either an integer or a tuple corresponding to each file.

# Examples

```jldoctest
julia> frame = [1.0 2.2 3.3 4.5];

julia> bias = [0.0 0.2 0.3 0.5];

julia> subtract_bias(frame, bias)
1×4 Matrix{Float64}:
 1.0  2.0  3.0  4.0

```

# See Also

[`subtract_bias!`](@ref)
