```
frobenius_distance(ρ::Union{MPO, LPDO}, σ::Union{MPO, LPDO})
```

Compute the trace norm of the difference between two LPDOs or MPOs:

$$
T(\rho,\sigma) = \sqrt{\text{Tr}\big[(\rho-\sigma)^\dagger(\rho-\sigma)\big]}
$$
