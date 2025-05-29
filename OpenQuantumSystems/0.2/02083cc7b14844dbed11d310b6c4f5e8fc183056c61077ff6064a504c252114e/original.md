```
tracenorm_nh(rho)
```

Trace norm of `rho`. Note that in this case `rho` doesn't have to be represented by a square matrix (i.e. it can have different left-hand and right-hand bases). It uses the identity

$$
    T(ρ) = \operatorname{tr}\{\sqrt{ρ^† ρ}\} = \sum_i σ_i
$$

where $σ_i$ are the singular values of `rho`.
