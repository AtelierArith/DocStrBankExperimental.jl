```
RegularizedBoseKernel <: AbstractKernel
```

Regularized bosonic analytical continuation kernel.

In dimensionless variables $x = 2 τ/β - 1$, $y = β ω/Λ$, the fermionic integral kernel is a function on $[-1, 1] × [-1, 1]$:

$$
    K(x, y) = y \frac{e^{-Λ y (x + 1) / 2}}{e^{-Λ y} - 1}
$$

Care has to be taken in evaluating this expression around $y = 0$.
