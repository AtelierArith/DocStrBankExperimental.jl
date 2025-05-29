```
invwarpedview(img, tinv, [indices], [degree = Linear()], [fill = NaN]) -> wv
```

Create a view of `img` that lazily transforms any given index `I` passed to `wv[I]` to correspond to `img[inv(tinv)(I)]`. While technically this approach is known as backward mode warping, note that `InvWarpedView` is created by supplying the forward transformation. The given transformation `tinv` must accept a `SVector` as input and support `inv(tinv)`. A useful package to create a wide variety of such transformations is [CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl).

When invoking `wv[I]`, values for `img` must be reconstructed at arbitrary locations `inv(tinv)(I)`. `InvWarpedView` serves as a wrapper around [`WarpedView`](@ref) which takes care of interpolation and extrapolation. The parameters `degree` and `fill` can be used to specify the b-spline degree and the extrapolation scheme respectively.

The optional parameter `indices` can be used to specify the domain of the resulting `wv`. By default the indices are computed in such a way that `wv` contains all the original pixels in `img`.
