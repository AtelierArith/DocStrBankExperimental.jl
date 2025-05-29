```
kpol(X, Y; kwargs...)
```

Compute a polynomial kernel Gram matrix. 

  * `X` : X-data (n, p).
  * `Y` : Y-data (m, p).

Keyword arguments:

  * `gamma` : Scale of the polynom.
  * `coef0` : Offset of the polynom.
  * `degree` : Degree of the polynom.

Given matrices `X` and `Y` of sizes (n, p) and (m, p),  respectively, the function returns the (n, m) Gram matrix:

  * K(X, Y) = Phi(X) * Phi(Y)'.

The polynomial kernel between two vectors x and y is  computed by (`gamma` * (x' * y) + `coef0`)^`degree`.

## References

Scholkopf, B., Smola, A.J., 2002. Learning with kernels: support  vector machines, regularization, optimization, and beyond, Adaptive  computation and machine learning. MIT Press, Cambridge, Mass.

## Examples

```julia
using Jchemo
X = rand(5, 3)
Y = rand(2, 3)
kpol(X, Y; gamma = .1, coef0 = 10, degree = 3)
```
