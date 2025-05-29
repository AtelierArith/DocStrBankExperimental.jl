```
demand_bound(τ::AbstractRealTimeTask, t)
```

タスク `τ` のバーアの需要境界関数 (DBF) を計算します。

$$
\max\left(0, \left\lfloor \frac{t - \mathrm{deadline}(τ)}{\mathrm{period}(τ)} + 1 \right\rfloor \mathrm{cost}(τ) \right)
$$
