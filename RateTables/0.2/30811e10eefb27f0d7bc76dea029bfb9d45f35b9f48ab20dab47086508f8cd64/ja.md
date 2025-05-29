```
hmd_rates
```

男女両方の国の毎日の危険率を提供するRateTableです。これらは[Human Mortality Database](https://www.mortality.org/)からの年間死亡確率（qₓ's）に基づいています。

`country ∈ keys(hmd_countries)`および`sex ∈ (:male, :female, :total)`でセグメント化されています。

国コードのリストは、[`hmd_countries`](@ref)定数に詳細が記載されています。
