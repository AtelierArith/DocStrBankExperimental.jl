```
quantilecint(pd::DependentScalingModel, data::IDFdata, d::Real, p::Real, α::Real=.05)
```

レベル `p` の分位数のレベル (1-`α`) の近似ワルド分位数信頼区間を、期間 `d` に対して計算します。
