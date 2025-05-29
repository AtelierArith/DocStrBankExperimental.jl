```
tracedistance_nh(rho, sigma)
```

`rho` と `sigma` の間のトレース距離。ここで `rho` と `sigma` は正方行列で表される必要はありません（すなわち、左辺と右辺の基底が異なっていても構いません）。次の恒等式を使用します。

$$
    T(ρ,σ) = \frac{1}{2} \operatorname{tr}\{\sqrt{(ρ - σ)^† (ρ - σ)}\}
         = \frac{1}{2} \sum_i σ_i
$$

ここで $σ_i$ は `rho` - `sigma` の特異値です。
