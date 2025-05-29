```
mapwindow(f::F, img, window; 
    border = "replicate",
    indices = default_imginds(img, window, border), callmode=:copy!)
```

Apply `f` to sliding windows of `img``, with window size or axes specified by window. For example,`mapwindow(median!, img, window)`returns an Array of values similar to`img`(median-filtered, of course), whereas`mapwindow(extrema, img, window)`returns an Array of (min, max) tuples over a window of size window centered on each point of`img`.

The function `f` receives a buffer `buf`` for the window of data surrounding the current point.

If `window`` is specified as a Dims-tuple (tuple-of-integers), then all the integers must be odd and the window is centered around the current image point. 

For example, if `window = (3,3)`, then `f` will receive an Array `buf``corresponding to offsets (-1:1, -1:1) from the`imgf[i, j]``for which this is currently being computed. Alternatively, window can be a tuple of`AbstractUnitRange`s, in which case the specified ranges are used for`buf`; this allows you to use asymmetric windows if needed.

## Restricting to a subimage

The `indices` keyword allows you to omit unnecessary computations, if you want to do things like `mapwindow` on a subimage, or a strided variant of mapwindow.

This call:

```julia
mapwindow(f, img, window, indices=(2:5, 1:2:7))
```

is more efficient than the equivalent:

```julia
mapwindow(f, img, window)[2:5, 1:2:7]
```

because it omits computation of the unused values.

Because the data in the buffer `buf` that is received by `f` is copied from `img`, and the buffer's memory is reused, `f` should not return references to `buf`.

This code:

```julia
f = buf -> copy(buf) # as opposed to f = buf -> buf
mapwindow(f, img, window, indices=(2:5, 1:2:7))
```

would work as expected.

For functions that can only take `AbstractVector` inputs, you might have to first specialize `default_shape`:

```julia
f = v -> quantile(v, 0.75)
ImageFiltering.MapWindow.default_shape(::typeof(f)) = vec
```

and then `mapwindow(f, img, (m, n))` should filter at the 75th quantile.

See also: [`imfilter`](@ref).
