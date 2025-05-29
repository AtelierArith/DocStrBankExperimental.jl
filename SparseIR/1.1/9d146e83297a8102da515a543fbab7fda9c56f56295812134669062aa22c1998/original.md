```
LogisticKernel <: AbstractKernel
```

Fermionic/bosonic analytical continuation kernel.

In dimensionless variables $x = 2 τ/β - 1$, $y = β ω/Λ$, the integral kernel is a function on $[-1, 1] × [-1, 1]$:

$$
    K(x, y) = \frac{e^{-Λ y (x + 1) / 2}}{1 + e^{-Λ y}}
$$

LogisticKernel is a fermionic analytic continuation kernel. Nevertheless, one can model the $τ$ dependence of a bosonic correlation function as follows:

$$
    ∫ \frac{e^{-Λ y (x + 1) / 2}}{1 - e^{-Λ y}} ρ(y) dy = ∫ K(x, y) ρ'(y) dy,
$$

with

$$
    ρ'(y) = w(y) ρ(y),
$$

where the weight function is given by

$$
    w(y) = \frac{1}{\tanh(Λ y/2)}.
$$
