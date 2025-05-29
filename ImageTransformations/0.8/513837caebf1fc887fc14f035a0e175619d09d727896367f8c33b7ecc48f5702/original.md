```
warp(img, tform, [indices], [degree = Linear()], [fill = NaN]) -> imgw
```

Transform the coordinates of `img`, returning a new `imgw` satisfying `imgw[I] = img[tform(I)]`. This approach is known as backward mode warping. The transformation `tform` must accept a `SVector` as input. A useful package to create a wide variety of such transformations is [CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl).

# Reconstruction scheme

During warping, values for `img` must be reconstructed at arbitrary locations `tform(I)` which do not lie on to the lattice of pixels. How this reconstruction is done depends on the type of `img` and the optional parameter `degree`.

When `img` is a plain array, then on-grid b-spline interpolation will be used. It is possible to configure what degree of b-spline to use with the parameter `degree`. For example one can use `degree = Linear()` for linear interpolation, `degree = Constant()` for nearest neighbor interpolation, or `degree = Quadratic(Flat())` for quadratic interpolation.

In the case `tform(I)` maps to indices outside the original `img`, those locations are set to a value `fill` (which defaults to `NaN` if the element type supports it, and `0` otherwise). The parameter `fill` also accepts extrapolation schemes, such as `Flat()`, `Periodic()` or `Reflect()`.

For more control over the reconstruction scheme –- and how beyond-the-edge points are handled –- pass `img` as an `AbstractInterpolation` or `AbstractExtrapolation` from [Interpolations.jl](https://github.com/JuliaMath/Interpolations.jl).

The keyword `method` now also takes any InterpolationType from Interpolations.jl or a Degree, which is used to define a BSpline interpolation of that degree, in order to set the interpolation method used.

# The meaning of the coordinates

The output array `imgw` has indices that would result from applying `inv(tform)` to the indices of `img`. This can be very handy for keeping track of how pixels in `imgw` line up with pixels in `img`.

If you just want a plain array, you can "strip" the custom indices with `parent(imgw)`.

# Examples: a 2d rotation (see JuliaImages documentation for pictures)

```
julia> using Images, CoordinateTransformations, Rotations, TestImages, OffsetArrays

julia> img = testimage("lighthouse");

julia> axes(img)
(Base.OneTo(512),Base.OneTo(768))

# Rotate around the center of `img`
julia> tfm = recenter(RotMatrix(-pi/4), center(img))
AffineMap([0.707107 0.707107; -0.707107 0.707107], [-196.755,293.99])

julia> imgw = warp(img, tfm);

julia> axes(imgw)
(-196:709,-68:837)

# Alternatively, specify the origin in the image itself
julia> img0 = OffsetArray(img, -30:481, -384:383);  # origin near top of image

julia> rot = LinearMap(RotMatrix(-pi/4))
LinearMap([0.707107 -0.707107; 0.707107 0.707107])

julia> imgw = warp(img0, rot);

julia> axes(imgw)
(-293:612,-293:611)

julia> imgr = parent(imgw);

```

jldoctest using ImageTransformations, CoordinateTransformations, Rotations, TestImages, OffsetArrays using OffsetArrays: IdOffsetRange img = testimage("lighthouse") # axes (1:512, 1:768)

tfm = recenter(RotMatrix(-pi/4), center(img)) imgw = warp(img, tfm)

axes(imgw)

# output

(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837)) ```
