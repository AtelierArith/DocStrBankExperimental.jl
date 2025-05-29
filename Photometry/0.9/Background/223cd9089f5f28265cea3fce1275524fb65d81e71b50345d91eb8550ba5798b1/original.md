```
estimate_background(data, box_size;
    location=SourceExtractorBackground(),
    rms=StdRMS(),
    itp=ZoomInterpolator(box_size),
    edge_method=:pad,
    [filter_size])
```

Perform 2D background estimation using the given estimators mapped over windows of the data.

This function will estimate backgrounds in boxes of size `box_size`. When `size(data)` is not an integer multiple of the box size, there are two edge methods: `:pad` and `:crop`. The default is to pad (and is recommend to avoid losing image data). If `box_size` is an integer, the implicit shape will be square (eg. `box_size=4` is equivalent to `box_size=(4,4)`).

For evaluating the meshes, each box will be passed into `location` to estimate the background and then into `rms` to estimate the background root-mean-square value. These can be anything that is callable, like `median` or one of our [Background Estimators](@ref).

Once the meshes are created they will be median filtered if `filter_size` is given. `filter_size` can be either an integer or a tuple, with the integer being converted to a tuple the same way `box_size` is. Filtering is done via `ImageFiltering.MapWindow.mapwindow`. `filter_size` must be odd.

After filtering (if applicable), the meshes are passed to the `itp` to recreate a low-order estimate of the background at the same resolution as the input.

!!! note
    If your `box_size` is not an integer multiple of the input size, the output background and rms arrays will not have the same size.


# See Also

  * [Location Estimators](@ref), [RMS Estimators](@ref), [Interpolators](@ref)
