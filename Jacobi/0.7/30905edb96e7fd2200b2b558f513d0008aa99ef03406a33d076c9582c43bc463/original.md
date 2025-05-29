Gauss-type quadrature

Numerical integrals in the domain [-1,1] can be computed from knowledge of the function in a set of nodes and the corresponding nodes, such that

$$
\int_{-1}^1 (1-x)^a (1+x)^b (1-xf(x)\:dx \approx \sum_{i=1}^N w^{a,b}_i f(x_i)
$$

The parameters `a` and `b` form a famility of quadrature rules. But if one or both of the ends are specified, other quadrature families are possible:

  * No ends are specified, Gauss-Jacobi quadrature (GJ)
  * Both ends are specified, Gauss-Lobatto-Jacobi quadrature (GLJ)
  * A single end is specified, Gauss-Radau-Jacobi quadrature (if +1 is specified, GRJP, if -1, GRJM)

To compute the nodes, the following functions are available:

  * `zgj` (Gauss-Jacobi)
  * `zglj` (Gauss-Lobatto-Jacobi)
  * `zgrjm` (Gauss-Radau-Jacobi, -1)
  * `zgrjp` (Gauss-Radau-Jacobi, +1)

All these functions have the following parameters:

  * `Q`  Number of quadrature nodes
  * `a` (a) weight
  * `b` (b) weight
  * type Data type to be used, `Float64` is the default

To compute the weights, first the zeros (`z`) should be computed and then the weights are computed with the following functions:

  * `wgj(z, a, b)`
  * `wglj(z, a, b)`
  * `wgrjm(z, a, b)`
  * `wgrjp(z, a, b)`

### Derivatives

The nodes used in the quadrature rules are convenient when using high order Lagrange interpolation To compute derivatives. The following functions are used to compute the derivative matrix such that `du = D*u`:

  * `dgj(z, a, b)`
  * `dglj(z, a, b)`
  * `dgrjm(z, a, b)`
  * `dgrjp(z, a, b)`

### Examples

See the notebooks availbale with the package.
