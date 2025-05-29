```
integrate(u::PointData,cache::BasicILMCache,i::Int)
```

Calculate the discrete surface integral of scalar data `u` on the immersed points in `cache`, on body `i` in the body list in `cache`. This uses trapezoidal rule quadrature. If `u` is `VectorData`, then this returns a vector of the integrals in each coordinate direction. This operation produces the same effect, regardless if `cache` is set up for `GridScaling` or `IndexScaling`. In both cases, the surface element areas are used.
