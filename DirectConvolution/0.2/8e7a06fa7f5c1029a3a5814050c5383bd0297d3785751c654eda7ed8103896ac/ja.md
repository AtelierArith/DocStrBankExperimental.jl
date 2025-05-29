```
function apply_SG_filter2D(signal::Array{T,2},
                           sg_I::SG_Filter{T},
                           sg_J::SG_Filter{T};
                           derivativeOrder_I::Int=0,
                           derivativeOrder_J::Int=0,
                           min_I_BE::Type{<:BoundaryExtension}=ConstantBE,
                           max_I_BE::Type{<:BoundaryExtension}=ConstantBE,
                           min_J_BE::Type{<:BoundaryExtension}=ConstantBE,
                           max_J_BE::Type{<:BoundaryExtension}=ConstantBE)
```

2D Savitzky-Golayを適用し、平滑化された信号を返します。
