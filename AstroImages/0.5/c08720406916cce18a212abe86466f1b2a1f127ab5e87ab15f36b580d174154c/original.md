```
imview(img; clims=Percent(99.5), stretch=identity, cmap=:magma, contrast=1.0, bias=0.5)
```

Create a read only view of an array or AstroImageMat mapping its data values to Colors according to `clims`, `stretch`, and `cmap`.

The data is first clamped to `clims`, which can either be a tuple of (min, max) values or a function accepting an iterator of pixel values that returns (min, max). By default, `clims=Percent(99.5)` which sets the display min and max to the central 99.5 percentile range of pixel values. Convenient functions to use for `clims` are: `extrema`, `Zscale`, and `Percent(p)`

Next, the data is rescaled to [0,1] and remapped according to the function `stretch`. Stretch can be any monotonic fuction mapping values in the range [0,1] to some range [a,b]. Note that `log(0)` is not defined so is not directly supported. For a list of convenient stretch functions, see: `logstretch`, `powstretch`, `squarestretch`, `asinhstretch`, `sinhstretch`, `powerdiststretch`

Finally the data is mapped to RGB values according to `cmap`. If cmap is `nothing`, grayscale is used. ColorSchemes.jl defines hundreds of colormaps. A few nice ones for images include: `:viridis`, `:magma`, `:plasma`, `:thermal`, and `:turbo`.

Crucially, this function returns a view over the underlying data. If `img` is updated then those changes will be reflected by this view with the exception of `clims` which is not recalculated.

Note: if clims or stretch is a function, the pixel values passed in are first filtered to remove non-finite or missing values.

### Defaults

The default values of `clims`, `stretch`, and `cmap` are `extrema`, `identity`, and `nothing` respectively. You may alter these defaults using `AstroImages.set_clims!`,  `AstroImages.set_stretch!`, and `AstroImages.set_cmap!`.

### Automatic Display

Arrays wrapped by `AstroImageMat()` get displayed as images automatically by calling `imview` on them with the default settings when using displays that support showing PNG images.

### Missing data

Pixels that are `NaN` or `missing` will be displayed as transparent when `cmap` is set or black if. +/- Inf will be displayed as black or white respectively.

### Exporting Images

The view returned by `imview` can be saved using general `FileIO.save` methods. Example:

```julia
v = imview(data, cmap=:magma, stretch=asinhstretch, clims=Percent(95))
save("output.png", v)
```
