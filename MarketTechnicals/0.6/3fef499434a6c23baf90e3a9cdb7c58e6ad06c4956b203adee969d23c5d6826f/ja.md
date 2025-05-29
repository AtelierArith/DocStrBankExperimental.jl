```
vwap(ohlcv, n = 10; price = :Close, v = :Volume)
```

ボリューム加重平均価格

# 公式

$$
P = \frac{\sum_j P_j V_j}{\sum_j V_j}
$$
