```
integrate(u::PointData,ds::ScalarData)
```

Calculate the discrete surface integral of data `u`, using the surface element areas in `ds`. This uses trapezoidal rule quadrature. If `u` is `VectorData`, then this returns a vector of the integrals in each coordinate direction.
