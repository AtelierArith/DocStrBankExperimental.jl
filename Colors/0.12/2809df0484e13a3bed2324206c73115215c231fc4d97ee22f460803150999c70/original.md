```
DE_94()
DE_94(kl, kc, kh)
```

Construct a metric of CIE Delta E 94 recommendation (1994), with weighting parameters `kl`, `kc` and `kh` as provided for in the recommendation. When not provided, these parameters default to `1`. The `DE_94` is more perceptually uniform than the [`DE_AB`](@ref), but has some non-uniformities resolved by the [`DE_2000`](@ref).
