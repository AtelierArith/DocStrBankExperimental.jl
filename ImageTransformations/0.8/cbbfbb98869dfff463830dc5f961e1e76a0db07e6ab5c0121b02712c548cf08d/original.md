```
imrotate(img, θ, [indices], [degree = Linear()], [fill = NaN]) -> imgr
```

Rotate image `img` by `θ`∈[0,2π) in a clockwise direction around its center point. To rotate the image counterclockwise, specify a negative value for angle.

By default, rotated image `imgr` will not be cropped. Bilinear interpolation will be used and values outside the image are filled with `NaN` if possible, otherwise with `0`.

# Examples

```julia
julia> img = testimage("cameraman")

# rotate with bilinear interpolation but without cropping
julia> imrotate(img, π/4)

# rotate with bilinear interpolation and with cropping
julia> imrotate(img, π/4, axes(img))

# rotate with nearest interpolation but without cropping
julia> imrotate(img, π/4, Constant())

The keyword `method` now also takes any InterpolationType from Interpolations.jl
or a Degree, which is used to define a BSpline interpolation of that degree, in
order to set the interpolation method used during image rotation.

```

julia

# rotate with Linear interpolation without cropping

julia> imrotate(img, π/4, method = Linear())

# rotate with Lanczos4OpenCV interpolation without cropping

julia> imrotate(img, π/4, method = Lanczos4OpenCV()) ```

See also [`warp`](@ref).
