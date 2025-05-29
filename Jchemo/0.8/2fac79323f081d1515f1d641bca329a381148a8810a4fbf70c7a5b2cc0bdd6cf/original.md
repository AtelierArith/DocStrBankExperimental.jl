```
krbf(X, Y; kwargs...)
```

Compute a Radial-Basis-Function (RBF) kernel Gram matrix. 

  * `X` : X-data (n, p).
  * `Y` : Y-data (m, p).

Keyword arguments:

  * `gamma` : Scale parameter.

Given matrices `X` and `Y` of sizes (n, p) and (m, p),  respectively, the function returns the (n, m) Gram matrix:

  * K(X, Y) = Phi(X) * Phi(Y)'.

The RBF kernel between two vectors x and y is computed by  exp(-`gamma` * ||x - y||^2).

## References

Scholkopf, B., Smola, A.J., 2002. Learning with kernels: support  vector machines, regularization, optimization, and beyond, Adaptive  computation and machine learning. MIT Press, Cambridge, Mass.

## Examples

```julia
using Jchemo
X = rand(5, 3)
Y = rand(2, 3)
krbf(X, Y; gamma = .1)
```
