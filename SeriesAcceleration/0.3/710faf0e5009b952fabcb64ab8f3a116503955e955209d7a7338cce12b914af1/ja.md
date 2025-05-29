```
rateOfConv(arr:AbstractArray{T, 1})
```

配列から収束率 $\alpha_n = \frac{\log |(x_{n+1} - x_n)/(x_n - x_{n-1})|}{\log |(x_n - x_{n-1})/(x_{n-1}-x_{n-2})|}$ を推定します。`trace` を true に設定すると、すべての部分和の roc を取得できます。
