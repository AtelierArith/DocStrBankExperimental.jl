```
request_bound(τ::AbstractRealTimeTask, t)
```

タスク `τ` のリクエストバウンド関数 (RBF) を計算します。

$$
\left\lceil \frac{t}{\mathrm{period}(τ)}\right\rceil \mathrm{cost}(τ)
$$
