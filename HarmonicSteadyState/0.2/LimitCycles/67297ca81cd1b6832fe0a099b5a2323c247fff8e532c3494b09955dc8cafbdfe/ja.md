```
add_pairs!(eom::DifferentialEquation; ω_lc::Num, n=1)
```

システムにリミットサイクルハーモニクス `ω_lc` を追加します。これは、既存の ω ごとに n 組のハーモニクス ω ± ω_lc を追加することに相当します。
