```
FFTAxis <: AbstractVector{Int}
```

The one-dimensional counterpart to `FFTIndices`, supporting only a single dimension. Its elements are plain `Int` types rather than the `CartesianIndex` of `FFTIndices`.

This type serves as an analog to `Base.OneTo` which is usually returned by `axes`; this package provides `fftaxes` to serve the same purpose.

# Examples

```
julia> FFTAxis(4)
4-element FFTAxis:
 0
 1
 -2
 -1
```
