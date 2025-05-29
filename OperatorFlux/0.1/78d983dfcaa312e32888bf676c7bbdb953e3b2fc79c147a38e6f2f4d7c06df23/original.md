```
SpectralConv(transform, channels; init = glorot_uniform)
```

Constructs a spectral convolution operator with spectral transform `trafo`, channels `channels`,  and initialization function `init`.

# Example

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> conv = SpectralConv(trafo, channels)
```
