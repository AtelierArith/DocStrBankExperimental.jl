```
周波数推定(X::NEAT, Y::NEAT; w₁ = length(X.rawX) / (length(X.rawX) + length(Y.rawX)), w₂ = 1.0 - w₁)
```

周波数推定の等百分位等化を行います。これは、両方の集団において、各共通部分スコアに与えられた総スコアの条件付き分布が同じであると仮定します。
