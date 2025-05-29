```
atr(ohlc::TimeArray, n = 14; h= :High, l= :Low, c = :Close)
```

平均真の範囲

それは[`truerange`](@ref)の指数移動平均です。

# 公式

$$
\text{ATR} = \text{EMA}(\text{TR}, n)
$$
