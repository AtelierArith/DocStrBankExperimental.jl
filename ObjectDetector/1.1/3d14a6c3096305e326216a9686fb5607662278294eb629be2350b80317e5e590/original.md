```
prepare_image(img::AbstractArray{T}, model::U) where {T<:ImageCore.Colorant, U<:AbstractModel}
prepare_image(img::AbstractArray{T}, img_resized_size::Tuple, kern) where {T<:ImageCore.Colorant}
prepare_image!(dest_arr::AbstractArray{Float32}, img::AbstractArray{T}, kern) where {T<:Real}
prepare_image!(dest_arr::AbstractArray{Float32}, img::AbstractArray{T}, kern) where {T<:ImageCore.Colorant}
```

Loads and prepares (resizes + pads) an image to fit within a given shape. Input images should be column-major (julia default), and will be converted to row-major (darknet).
