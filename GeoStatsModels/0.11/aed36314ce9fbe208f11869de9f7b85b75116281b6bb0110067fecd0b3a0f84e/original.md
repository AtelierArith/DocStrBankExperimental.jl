```
IDW(exponent=1, distance=Euclidean())
```

The inverse distance weighting model introduced in the very early days of geostatistics by Shepard 1968.

The weights are computed as `λᵢ = 1 / d(x, xᵢ)ᵉ` for a given `distance` denoted by `d` and `exponent` denoted by `e`.

## References

  * Shepard 1968. [A two-dimensional interpolation function for irregularly-spaced data](https://dl.acm.org/doi/10.1145/800186.810616)
