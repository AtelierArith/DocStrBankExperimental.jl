```
atr(ohlc::TimeArray, n = 14; h= :High, l= :Low, c = :Close)
```

Average True Range

It's the exponential moving average of [`truerange`](@ref)

# Formula

$$
\text{ATR} = \text{EMA}(\text{TR}, n)
$$
