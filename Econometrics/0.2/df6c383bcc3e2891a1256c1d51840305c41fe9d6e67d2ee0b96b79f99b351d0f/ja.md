```
confint(obj::EconometricModel; se::AbstractVector{<:Real} = stderror(obj), level::Real = 0.95)
```

係数の信頼区間を計算します。信頼水準は `level` で指定します（デフォルトは95%）。`se` は事前に計算された値を指定できます。
