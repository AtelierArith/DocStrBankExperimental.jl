```
tracedistance_h(rho, sigma)
```

`rho` と `sigma` の間のトレース距離。次の恒等式を使用します。

$$
T(ρ,σ) = \frac{1}{2} \operatorname{tr}\{\sqrt{(ρ - σ)^† (ρ - σ)}\} = \frac{1}{2} \sum_i |λ_i|
$$

ここで、$λ_i$ は `rho` - `sigma` の固有値です。
