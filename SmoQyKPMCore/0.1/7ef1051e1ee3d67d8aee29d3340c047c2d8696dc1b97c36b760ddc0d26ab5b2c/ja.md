```
kpm_dot(
    coefs::T, moments::T
) where {T<:AbstractVector}
```

内積を計算します

$$
\langle c | \mu \rangle = \sum_{m=1}^M c_m \cdot \mu_m,
$$

ここで、$c_m$ はKPM展開係数、$\mu_m$ はKPMモーメントです。
