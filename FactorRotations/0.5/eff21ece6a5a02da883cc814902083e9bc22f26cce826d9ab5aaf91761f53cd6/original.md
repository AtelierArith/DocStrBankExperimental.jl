```
Geomin(epsilon = 0.01)
```

The *Geomin* rotation method.

## Details

The *Geomin* is an oblique rotation method that minimizes the sum of column-wise geometric means of the squared loadings:

$$
Q_{\mathrm{Geomin}}(Λ, ε) =
    ∑_{i = 1}^p \left(\prod_{j = 1}^k λ²_{i, j} + ε \right)^{\frac{1}{k}}.
$$

## Keyword arguments

  * `epsilon`: A small non-negative constant to deal with zero loadings.
