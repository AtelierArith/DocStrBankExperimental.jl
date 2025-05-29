```
compute_compressibility(sol::OZSolution, system::SimpleLiquid)
```

Computes the isothermal compressibility χ of the system

uses the formula 1/ρkBTχ = 1 - ρ ĉ(k=0) for single component systems and 1/ρkBTχ = 1 - ρ Σᵢⱼ ĉᵢⱼ(k=0) for mixtures.  Eq. (3.6.16) in Hansen and McDonald
