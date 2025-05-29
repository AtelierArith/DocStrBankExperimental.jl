```
struct TimeDifferential
    recGeom
```

時間次元に沿って適用される次数 `K` の微分演算子。`k` が次数であるフィルタ `w^k` を適用します。例えば、時間微分は `TimeDifferential{1}` であり、時間積分は `TimeDifferential{-1}` です。

# コンストラクタ

```
judiTimeIntegration(recGeom, order)
judiTimeIntegration(judiVector, order)

judiTimeDerivative(recGeom, order)
judiTimeDerivative(judiVector, order)
```
