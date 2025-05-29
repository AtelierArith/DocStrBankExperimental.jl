```
kpm_dot(
    kpm_expansion::KPMExpansion, moments::AbstractVector
)
```

内積を計算します

$$
\langle c | \mu \rangle = \sum_{m=1}^M c_m \cdot \mu_m,
$$

ここで、$c_m$ は KPM 拡張係数であり、$\mu_m$ はモーメントです。モーメントの計算方法については [`kpm_moments`](@ref) を参照してください。
