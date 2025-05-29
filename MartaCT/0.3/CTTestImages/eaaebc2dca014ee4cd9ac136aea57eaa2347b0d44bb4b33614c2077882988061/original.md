```
combine_images(imp::ImageParams{T}, rect::AbstractMatrix{T}, circle::AbstractMatrix{T}) where {T}
```

Helper function to create a gray scale image.

Combine the `rect` image with the `circle` image for calibration. The circle image should be smaller than the gray scale image!

See also: [`gray_scale_image`](@ref), [`circle_image`](@ref)
