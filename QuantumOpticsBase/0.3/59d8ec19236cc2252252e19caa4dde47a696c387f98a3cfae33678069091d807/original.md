```
tracedistance_h(rho, sigma)
```

Trace distance between `rho` and `sigma`.

It uses the identity

$$
T(ρ,σ) = \frac{1}{2} Tr\{\sqrt{(ρ - σ)^† (ρ - σ)}\} = \frac{1}{2} \sum_i |λ_i|
$$

where $λ_i$ are the eigenvalues of `rho` - `sigma`.
