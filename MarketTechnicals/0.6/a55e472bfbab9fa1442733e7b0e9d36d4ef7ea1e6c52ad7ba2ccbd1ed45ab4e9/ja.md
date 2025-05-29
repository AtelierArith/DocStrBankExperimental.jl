```
chaikinvolatility(ta, n = 10, p = 10; h = High, l = :Low)
```

チャイキンボラティリティ

# 引数

  * `n` はスムーズ期間です
  * `p` は前の期間です

# 公式

$$
\text{Chaikin Vola} =
  \frac{\text{EMA}(P^\text{High}_t - P^\text{Low}_t, n) - \text{EMA}(P^\text{High}_{t-p} - P^\text{Low}_{t-p}, n)}
       {\text{EMA}(P^\text{High}_{t-p} - P^\text{Low}_{t-p}, n)}
  \times 100
$$

# 参考文献

  * [IncredibleCharts](https://www.incrediblecharts.com/indicators/chaikin_volatility.php)
