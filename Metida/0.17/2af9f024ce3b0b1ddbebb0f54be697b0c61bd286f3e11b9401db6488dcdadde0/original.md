```
dof_satter(lmm::LMM{T}, l) where T
```

Return Satterthwaite approximation for the denominator degrees of freedom, where `l` is a contrast vector (estimable linear combination of fixed effect coefficients vector (`β`).

$$
df = \frac{2(LCL')^{2}}{g'Ag}
$$

Where: $A = 2H^{-1}$, $g = \triangledown_{\theta}(LC^{-1}_{\theta}L')$
