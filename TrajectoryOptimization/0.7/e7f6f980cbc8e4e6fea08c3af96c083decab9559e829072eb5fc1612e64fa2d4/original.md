```
LQRCost(Q, R, xf, [uf; kwargs...])
```

Convenience constructor for a `QuadraticCostFunction` of the form:

$$
\frac{1}{2} (x-x_f)^T Q (x-xf) + \frac{1}{2} (u-u_f)^T R (u-u_f)
$$

If $Q$ and $R$ are diagonal, the output will be a `DiagonalCost`, otherwise it will be a `QuadraticCost`.
