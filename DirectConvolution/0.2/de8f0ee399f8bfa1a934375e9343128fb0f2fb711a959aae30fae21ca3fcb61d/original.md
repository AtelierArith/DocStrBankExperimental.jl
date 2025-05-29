```
function apply_SG_filter(signal::Array{T,1},
                         sg::SG_Filter{T};
                         derivativeOrder::Int=0,
                         left_BE::Type{<:BoundaryExtension}=ConstantBE,
                         right_BE::Type{<:BoundaryExtension}=ConstantBE)
```

Applies an 1D Savitzky-Golay and returns the smoothed signal.
