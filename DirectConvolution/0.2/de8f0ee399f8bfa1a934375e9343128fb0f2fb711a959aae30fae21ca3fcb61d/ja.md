```
function apply_SG_filter(signal::Array{T,1},
                         sg::SG_Filter{T};
                         derivativeOrder::Int=0,
                         left_BE::Type{<:BoundaryExtension}=ConstantBE,
                         right_BE::Type{<:BoundaryExtension}=ConstantBE)
```

1DのSavitzky-Golayを適用し、平滑化された信号を返します。
