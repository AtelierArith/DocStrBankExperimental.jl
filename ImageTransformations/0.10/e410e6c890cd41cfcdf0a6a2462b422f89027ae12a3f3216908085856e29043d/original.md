```
imresize(img, sz; [method]) -> imgr
imresize(img, inds; [method]) -> imgr
imresize(img; ratio, [method]) -> imgr
```

upsample/downsample the image `img` to a given size `sz` or axes `inds` using interpolations. If `ratio` is provided, the output size is then `ceil(Int, size(img).*ratio)`.

!!! tip
    This interpolates the values at sub-pixel locations. If you are shrinking the image, you risk aliasing unless you low-pass filter `img` first.


# Arguments

  * `img`: the input image array
  * `sz`: the size of output array
  * `inds`: the axes of output array If `inds` is passed, the output array `imgr` will be `OffsetArray`.

# Parameters

!!! info
    To construct `method`, you may need to load `Interpolations` package first.


  * `ratio`: the upsample/downsample ratio used. The output size is `ceil(Int, size(img).*ratio)`. If `ratio` is larger than `1`, it is an upsample operation. Otherwise it is a downsample operation. `ratio` can also be a tuple, in which case `ratio[i]` specifies the resize ratio at dimension `i`.
  * `method::InterpolationType`:  specify the interpolation method used for reconstruction. conveniently, `methold` can also be a `Degree` type, in which case a `BSpline` object will be created. For example, `method = Linear()` is equivalent to `method = BSpline(Linear())`.

# Examples

```julia
using ImageTransformations, TestImages, Interpolations

img = testimage("lighthouse") # 512*768

# pass integers as size
imresize(img, 256, 384) # 256*384
imresize(img, (256, 384)) # 256*384
imresize(img, 256) # 256*768

# pass indices as axes
imresize(img, 1:256, 1:384) # 256*384
imresize(img, (1:256, 1:384)) # 256*384
imresize(img, (1:256, )) # 256*768

# pass resize ratio
imresize(img, ratio = 0.5) #256*384
imresize(img, ratio = (2, 1)) # 1024*768

# use different interpolation method
imresize(img, (256, 384), method=Linear()) # 256*384 bilinear interpolation
imresize(img, (256, 384), method=Lanczos4OpenCV()) # 256*384 OpenCV-compatible Lanczos 4 interpolation
```

For downsample with `ratio=0.5`, [`restrict`](@ref) is a much faster two-fold implementation that you can use.
