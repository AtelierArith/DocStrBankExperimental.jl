```julia
positive_limiter(u, weights, ll, lr)
positive_limiter(u, weights, ll, lr, t0)

```

Slope limiter to preserve positivity

*R. Vandenhoeck and A. Lani. Implicit high-order flux reconstruction solver for high-speed compressible flows. Computer Physics Communications 242: 1-24, 2019."*

  * @arg u: conservative variables with solution points in dim1 and states in dim2
  * @arg γ: specific heat ratio
  * @arg weights: quadrature weights for computing mean value
  * @arg ll&lr: Langrange polynomials at left/right edge
  * @arg t0=1.0: minimum limiting slope
