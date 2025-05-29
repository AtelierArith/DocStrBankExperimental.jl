```
quantilecint(fd::MarginalScalingModel, data::IDFdata, d::Real, p::Real, α::Real=.05)
```

持続時間 `d` のレベル `q` の分位数の (1-`α`) レベルの近似ワルド分位数信頼区間を計算します。
