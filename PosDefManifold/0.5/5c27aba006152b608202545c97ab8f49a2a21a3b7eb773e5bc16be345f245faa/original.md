```julia
    midrange(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

Midrange (average of extremal values) of positive definite matrices $P$ and $Q$. Only the Fisher metric is supported, allowing the so-called *geometric midrange*. This has been defined in Mostajeran et *al.* (2019) [🎓](@ref) as

$P * Q = \frac{1}{\sqrt{\lambda_(min)}+\sqrt{\lambda_(max)}}\Big(Q+\sqrt{\lambda_(min)*\lambda_(max)}P\Big)$,

where $\lambda_(min)$ and $\lambda_(max)$ are the extremal generalized eigenvalues of $P$ and $Q$.

**Examples**

```julia
P=randP(3)
Q=randP(3)
M=midrange(Fisher, P, Q)
```
