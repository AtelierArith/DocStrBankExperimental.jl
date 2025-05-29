```
truerange(ohlc::TimeArray; h = :High, l = :Low, c = :Close)
```

真の範囲

# 公式

$$
\text{TR} = \max (P_t^\text{High}, P_{t-1}^\text{Close}) -
            \min (P_t^\text{Low},  P_{t-1}^\text{Close})
$$
