```
SymmetricRelativeEntropy <: ProbabilityDensityDM
```

Symmetric Relative Entropy discriminant measure for the Probability Density and Time Frequency energy maps. Similar idea to the Asymmetric Relative Entropy, but this aims to make the measure more symmetric.

Equation: Denote the Asymmetric Relative Entropy as $D_A(p,q)$, then

$D(p,q) = D_A(p,q) + D_A(q,p) = \sum p(x) \log \frac{p(x)}{q(x)} + q(x) \log \frac{q(x)}{p(x)}$

where $\int_{-\infty}^{\infty} p(t) dt = \int_{-\infty}^{\infty} q(t) dt = 1$ ($p(t)$ and $q(t)$ are probability density functions.)

**See also:** [`AsymmetricRelativeEntropy`](@ref)
