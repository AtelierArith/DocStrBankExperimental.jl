```
riemann_tensor(M::AbstractManifold, p, X, Y, Z)
```

Compute the value of the Riemann tensor $R(X_f,Y_f)Z_f$ at point `p`, where $X_f$, $Y_f$ and $Z_f$ are vector fields defined by parallel transport of, respectively, `X`, `Y` and `Z` to the desired point. All computations are performed using the connection associated to manifold `M`.

The formula reads $R(X_f,Y_f)Z_f = \nabla_X\nabla_Y Z - \nabla_Y\nabla_X Z - \nabla_{[X, Y]}Z$, where $[X, Y]$ is the Lie bracket of vector fields.

Note that some authors define this quantity with inverse sign.
