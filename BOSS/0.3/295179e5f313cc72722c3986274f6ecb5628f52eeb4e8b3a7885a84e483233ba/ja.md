```
x = maximize_acquisition(::BossProblem, ::AcquisitionFunction, ::AcquisitionMaximizer)
```

与えられた `acquisition` 関数を与えられた `acq_maximizer` アルゴリズムを使用して最大化し、最適な次の評価点を見つけます。

# キーワード

  * `options::BossOptions`: 様々な設定を定義します。
