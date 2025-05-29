```
integrate(u::PointData,ds::ScalarData,bl::BodyList,i::Int)
```

Calculate the discrete surface integral of scalar data `u`, restricting the integral to body `i` in body list `bl`, using the surface element areas in `ds`. This uses trapezoidal rule quadrature. If `u` is `VectorData`, then this returns a vector of the integrals in each coordinate direction.
