```
downsample(algorithm::MultiScaleAlgorithm, s::Int, x)
```

Downsample and coarse-grain `x` to scale `s` according to the given [`MultiScaleAlgorithm`](@ref). The return type depends on `algorithm`.
