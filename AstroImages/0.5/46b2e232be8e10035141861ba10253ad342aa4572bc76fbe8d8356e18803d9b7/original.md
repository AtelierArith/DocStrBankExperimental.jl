```
implot(
    img::AbstractArray;
    clims=Percent(99.5),
    stretch=identity,
    cmap=:magma,
    bias=0.5,
    contrast=1,
    wcsticks=true,
    grid=true,
    platescale=1
)
```

Create a read only view of an array or AstroImageMat mapping its data values to an array of Colors. Equivalent to:

```
implot(
    imview(
        img::AbstractArray;
        clims=Percent(99.5),
        stretch=identity,
        cmap=:magma,
        bias=0.5,
        contrast=1,
    ),
    wcsn=1,
    wcsticks=true,
    wcstitle=true,
    grid=true,
    platescale=1
)
```

### Image Rendering

See `imview` for how data is mapped to RGBA pixel values.

### WCS & Image Coordinates

If provided with an AstroImage that has WCS headers set, the tick marks and plot grid are calculated using WCS.jl. By default, use the first WCS coordinate system. The underlying pixel coordinates are those returned by `dims(img)` multiplied by `platescale`. This allows you to overplot lines, regions, etc. using pixel coordinates. If you wish to compute the pixel coordinate of a point in world coordinates, see `world_to_pix`.

  * `wcsn` (default `1`) select which WCS transform in the headers to use for ticks & grid
  * `wcsticks` (default `true` if WCS headers present) display ticks and labels, and title using world coordinates
  * `wcstitle` (default `true` if WCS headers present and `length(refdims(img))>0`). When slicing a cube, display the location along unseen axes in world coordinates instead of pixel coordinates.
  * `grid` (default `true`) show a grid over the plot. Uses WCS coordinates if `wcsticks` is true, otherwise pixel coordinates multiplied by `platescale`.
  * `platescale` (default `1`). Scales the underlying pixel coordinates to ease overplotting, etc. If `wcsticks` is false, the displayed pixel coordinates are also scaled.

### Defaults

The default values of `clims`, `stretch`, and `cmap` are `extrema`, `identity`, and `nothing` respectively. You may alter these defaults using `AstroImages.set_clims!`,  `AstroImages.set_stretch!`, and `AstroImages.set_cmap!`.
