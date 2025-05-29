```
metric(Y::GrassmannManifold, Δ₁::AbstractMatrix, Δ₂::AbstractMatrix)
```

Compute the metric for vectors `Δ₁` and `Δ₂` at `Y`. 

The representation of the Grassmann manifold is realized as a *quotient space of the Stiefel manifold*. 

The metric for the Grassmann manifold is:

$$
g^{Gr}_Y(\Delta_1, \Delta_2) = g^{St}_Y(\Delta_1, \Delta_2) = \mathrm{Tr}(\Delta_1^T (\mathbb{I} - Y Y^T) \Delta_2) = \mathrm{Tr}(\Delta_1^T \Delta_2),
$$

where we used that $Y^T\Delta_i$ for $i = 1, 2.$
