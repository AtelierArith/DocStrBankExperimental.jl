```
SpectralCovariance(transform, rank, channels; init = glorot_uniform)
```

Constructs a spectral covariance operator with spectral transform `trafo`, low-rank matrix rank `rank`, channels `channels`,  and initialization function `init`.

# Example

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> rank = 3
julia> conv = SpectralCovariance(trafo, rank, channels)
```
