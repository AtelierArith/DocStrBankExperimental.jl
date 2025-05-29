```
GaussLegendre{C, N, W}
```

Struct for evaluating an integral via (composite) Gauss-Legendre quadrature. The field `C` will be `true` if `subintervals > 1`, and `false` otherwise.

The fields `nodes::N` and `weights::W` are defined by `nodes, weights = gausslegendre(n)` for a given number of nodes `n`.

The field `subintervals::Int64 = 1` (with default value `1`) defines the number of intervals to partition the original interval of integration `[a, b]` into, splitting it into `[xⱼ, xⱼ₊₁]` for `j = 1,…,subintervals`, where `xⱼ = a + (j-1)h` and `h = (b-a)/subintervals`. Gauss-Legendre quadrature is then applied on each subinterval. For example, if `[a, b] = [-1, 1]` and `subintervals = 2`, then Gauss-Legendre quadrature will be applied separately on `[-1, 0]` and `[0, 1]`, summing the two results.
