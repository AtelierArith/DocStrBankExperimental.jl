```
frobenius_distance(ρ::Union{MPO, LPDO}, σ::Union{MPO, LPDO})
```

2つのLPDOまたはMPOの違いのトレースノルムを計算します：

$$
T(\rho,\sigma) = \sqrt{\text{Tr}\big[(\rho-\sigma)^\dagger(\rho-\sigma)\big]}
$$
