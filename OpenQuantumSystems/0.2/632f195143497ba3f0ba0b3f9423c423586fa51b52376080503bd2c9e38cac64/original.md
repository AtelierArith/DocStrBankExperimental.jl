```
tracedistance_nh(rho, sigma)
```

Trace distance between `rho` and `sigma`. Note that in this case `rho` and `sigma` don't have to be represented by square matrices (i.e. they can have different left-hand and right-hand bases). It uses the identity

$$
    T(ρ,σ) = \frac{1}{2} \operatorname{tr}\{\sqrt{(ρ - σ)^† (ρ - σ)}\}
         = \frac{1}{2} \sum_i σ_i
$$

where $σ_i$ are the singular values of `rho` - `sigma`.
