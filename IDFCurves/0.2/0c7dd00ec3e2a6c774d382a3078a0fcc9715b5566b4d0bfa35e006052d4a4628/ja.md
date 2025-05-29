```
quantilecint(pd::MarginalScalingModel, data::IDFdata, d::Real, p::Real, H::PDMat{<:Real}, α::Real=.05)
```

レベル (1-`α`) のワルド量子信頼区間を、期間 `d` のレベル `q` の量子に対して計算します。

## 詳細

この関数は、引数として提供されたヘッセ行列 `H` を使用します。  
