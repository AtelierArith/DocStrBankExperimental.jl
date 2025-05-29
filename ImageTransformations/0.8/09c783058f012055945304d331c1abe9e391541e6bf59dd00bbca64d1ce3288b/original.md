```
warpedview(img, tform, [indices], [degree = Linear()], [fill = NaN]) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` to correspond to `img[tform(I)]`. This approach is known as backward mode warping. The given transformation `tform` must accept a `SVector` as input. A useful package to create a wide variety of such transformations is [CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl).

When invoking `wv[I]`, values for `img` must be reconstructed at arbitrary locations `tform(I)` which do not lie on to the lattice of pixels. How this reconstruction is done depends on the type of `img` and the optional parameter `degree`. When `img` is a plain array, then on-grid b-spline interpolation will be used, where the pixel of `img` will serve as the coeficients. It is possible to configure what degree of b-spline to use with the parameter `degree`. The two possible values are `degree = Linear()` for linear interpolation, or `degree = Constant()` for nearest neighbor interpolation.

In the case `tform(I)` maps to indices outside the domain of `img`, those locations are set to a value `fill` (which defaults to `NaN` if the element type supports it, and `0` otherwise). Additionally, the parameter `fill` also accepts extrapolation schemes, such as `Flat()`, `Periodic()` or `Reflect()`.

The optional parameter `indices` can be used to specify the domain of the resulting `WarpedView`. By default the indices are computed in such a way that the resulting `WarpedView` contains all the original pixels in `img`. To do this `inv(tform)` has to be computed. If the given transformation `tform` does not support `inv`, then the parameter `indices` has to be specified manually.

`warpedview` is essentially a non-coping, lazy version of [`warp`](@ref). As such, the two functions share the same interface, with one important difference. `warpedview` will insist that the resulting `WarpedView` will be a view of `img` (i.e. `parent(warpedview(img, ...)) === img`). Consequently, `warpedview` restricts the parameter `degree` to be either `Linear()` or `Constant()`.
