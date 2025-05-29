```
change_representer(M::Hyperbolic, ::EuclideanMetric, p, X)
```

Change the Eucliden representer `X` of a cotangent vector at point `p`. We only have to correct for the metric, which means that the sign of the last entry changes, since for the result $Y$  we are looking for a tangent vector such that

$$
    g_p(Y,Z) = -y_{n+1}z_{n+1} + \sum_{i=1}^n y_iz_i = \sum_{i=1}^{n+1} z_ix_i
$$

holds, which directly yields $y_i=x_i$ for $i=1,\ldots,n$ and $y_{n+1}=-x_{n+1}$.
