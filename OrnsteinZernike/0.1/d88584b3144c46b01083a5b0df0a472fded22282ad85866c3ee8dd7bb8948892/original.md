```
compute_excess_energy(sol::OZSolution, system::SimpleLiquid)
```

Computes the excess energy per particle Eₓ, such that E = (dims/2*kBT + Eₓ)*N.

uses the formula Eₓ = 1/2 ρ ∫dr g(r) u(r) for single component systems and Eₓ = 1/2 ρ Σᵢⱼ xᵢxⱼ ∫dr gᵢⱼ(r) uᵢⱼ(r) for mixtures. Here x is the concentration fraction xᵢ=ρᵢ/sum(ρ).
