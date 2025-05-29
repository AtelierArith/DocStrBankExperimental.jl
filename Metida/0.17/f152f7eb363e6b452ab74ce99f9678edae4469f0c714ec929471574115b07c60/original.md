```
dof_satter(lmm::LMM{T}, l::Matrix) where T
```

Return Satterthwaite approximation for the denominator degrees of freedom for conrast matrix `l`.

For `size(l, 1)` > 1:

$$
df = \frac{2E}{E - rank(LCL')}
$$

where:

  * let $LCL' = QΛQ^{-1}$, where $QΛQ^{-1}$ - spectral decomposition of $LCL'$
  * $Lq_i$ is the i-th row of $Q^{-1}L$
  * $A = 2H^{-1}$, $g = \triangledown_{\theta}(Lq_i C^{-1}_{\theta} Lq_i')$
  * $v_i = \frac{2*Λ_{i,i}^2}{g' * A * g}$
  * $E = \sum_{i=1}^n {\frac{v_i}(v_i - 2)}$ for $v_i > 2$
