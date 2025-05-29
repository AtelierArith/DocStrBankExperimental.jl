```
compute_excess_energy(sol::OZSolution, system::SimpleLiquid)
```

粒子あたりの過剰エネルギー Eₓ を計算します。E = (dims/2*kBT + Eₓ)*N です。

単一成分系の場合の式 Eₓ = 1/2 ρ ∫dr g(r) u(r) と、混合物の場合の式 Eₓ = 1/2 ρ Σᵢⱼ xᵢxⱼ ∫dr gᵢⱼ(r) uᵢⱼ(r) を使用します。ここで x は濃度分率 xᵢ=ρᵢ/sum(ρ) です。
