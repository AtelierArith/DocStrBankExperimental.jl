```
compute_compressibility(sol::OZSolution, system::SimpleLiquid)
```

システムの等温圧縮率 χ を計算します

単一成分システムの場合は式 1/ρkBTχ = 1 - ρ ĉ(k=0) を使用し、混合物の場合は 1/ρkBTχ = 1 - ρ Σᵢⱼ ĉᵢⱼ(k=0) を使用します。Hansen と McDonald の式 (3.6.16)
