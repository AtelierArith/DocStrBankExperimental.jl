```
warp(img, tform, [indices]; kwargs...) -> imgw
```

Transform the coordinates of `img`, returning a new `imgw` satisfying `imgw[I] = img[tform(I)]`.

# Output

The output array `imgw` is an `OffsetArray`. Unless manually specified, `axes(imgw) == axes(img)` does not hold in general. If you just want a plain array, you can "strip" the custom indices with `parent(imgw)` or `OffsetArrays.no_offset_view(imgw)`.

# Arguments

  * `img`: the original image that you need coordinate transformation.
  * `tform`: the coordinate transformation function or function-like object, it must accept a [`SVector`](https://github.com/JuliaArrays/StaticArrays.jl) as input. A useful package to create a wide variety of such transfomrations is [CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl).
  * `indices` (Optional): specifies the output image axes. By default, the indices are computed in such a way that `imgw` contains all the original pixels in `img` using [`autorange`](@ref ImageTransformations.autorange). To do this `inv(tform)` has to be computed. If the given transfomration `tform` does not support `inv` then the parameter `indices` has to be specified manually.

# Parameters

!!! info
    To construct `method` and `fillvalue` values, you may need to load `Interpolations` package first.


  * `method::Union{Degree, InterpolationType}`: the interpolation method you want to use. By default it is `BSpline(Linear())`. To construct the method instance, one may need to load `Interpolations`.
  * `fillvalue`: the value that used to fill the new region. The default value is `NaN` if possible, otherwise is `0`. One can also pass the extrapolation boundary condition: `Flat()`, `Reflect()` and `Periodic()`.

# See also

There're some high-level interfaces of `warp`:

  * image rotation: [`imrotate`](@ref)
  * image resize: [`imresize`](@ref)

There are also lazy versions of `warp`:

  * [`WarpedView`](@ref) is almost equivalent to `warp` except that it does not allocate memory.
  * [`InvWarpedView(img, tform, [indices]; kwargs...)`](@ref ImageTransformations.InvWarpedView) is almost equivalent to `warp(img, inv(tform), [indices]; kwargs...)` except that it does not allocate memory.

# Extended help

## Parameters in detail

This approach is known as backward mode warping. It is called "backward" because the internal coordinate transformation is actually an inverse map from `axes(imgr)` to `axes(img)`.

You can manually specify interpolation behavior by constructing `AbstractExtrapolation` object and passing it to `warp` as `img`. However, this is usually cumbersome. For this reason, there are two keywords `method` and `fillvalue` to conveniently construct an `AbstractExtrapolation` object during `warp`.

!!! warning
    If `img` is an `AbstractExtrapolation`, then additional `method` and `fillvalue` keywords will be discarded.


### `method::Union{Degree, InterpolationType}`

The interpolation method you want to use to reconstruct values in the wrapped image.

Among those possible `InterpolationType` choice, there are some commonly used methods that you may have used in other languages:

  * nearest neighbor: `BSpline(Constant())`
  * triangle/bilinear: `BSpline(Linear())`
  * bicubic: `BSpline(Cubic(Line(OnGrid())))`
  * lanczos2: `Lanczos(2)`
  * lanczos3: `Lanczos(3)`
  * lanczos4: `Lanczos(4)` or `Lanczos4OpenCV()`

When passing a `Degree`, it is expected to be a `BSpline`. For example, `Linear()` is equivalent to `BSpline(Linear())`.

### `fillvalue`

In case `tform(I)` maps to indices outside the original `img`, those locations are set to a value `fillvalue`. The default fillvalue is `NaN` if the element type of `img` supports it, and `0` otherwise.

The parameter `fillvalue` can be either a `Number` or `Colorant`. In this case, it will be converted to `eltype(imgr)` first. For example, `fillvalue = 1` will be converted to `Gray(1)` which will fill the outside indices with white pixels.

Also, `fillvalue` can be extrapolation schemes: `Flat()`, `Periodic()` and `Reflect()`. The best way to understand these schemes is perhaps try it with small example:

```jldoctest
julia> using ImageTransformations, TestImages, Interpolations

julia> using OffsetArrays: IdOffsetRange

julia> img = testimage("lighthouse");

julia> imgr = imrotate(img, π/4; fillvalue=Flat()); # zero extrapolation slope

julia> imgr = imrotate(img, π/4; fillvalue=Periodic()); # periodic boundary

julia> imgr = imrotate(img, π/4; fillvalue=Reflect()); # mirror boundary

julia> axes(imgr)
(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837))
```

## The meaning of the coordinates

`imgw` keeps track of the indices that would result from applying `inv(tform)` to the indices of `img`. This can be very handy for keeping track of how pixels in `imgw` line up with pixels in `img`.

```jldoctest
julia> using ImageTransformations, TestImages, Interpolations

julia> img = testimage("lighthouse");

julia> imgr = imrotate(img, π/4);

julia> imgr_cropped = imrotate(img, π/4, axes(img));

julia> imgr[axes(img)...] == imgr_cropped # No need to manually calculate the offsets
true
```

!!! tip
    For performance consideration, it's recommended to pass the `inds` positional argument to `warp` instead of cropping the output with `imgw[inds...]`.


# Examples: a 2d rotation

!!! note
    This example only shows how to construct `tform` and calls `warp`. For common usage, it is recommended to use [`imrotate`](@ref) function directly.


Rotate around the center of `img`:

```jldoctest
julia> using ImageTransformations, CoordinateTransformations, Rotations, TestImages, OffsetArrays

julia> using OffsetArrays: IdOffsetRange

julia> img = testimage("lighthouse");

julia> axes(img)
(Base.OneTo(512), Base.OneTo(768))

julia> tfm = recenter(RotMatrix(-pi/4), center(img));

julia> imgw = warp(img, tfm);

julia> axes(imgw)
(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837))
```
