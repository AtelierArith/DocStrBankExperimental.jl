```
LocationScaleStatistic{S, M, P}
```

位置スケールファミリーに適用される統計量を表す可変構造体。

# フィールド

  * `stat::S`: 統計量。
  * `μ::M`: 位置パラメータ。
  * `Ω::P`: 分散の逆平方根。

# 例

```
STAT = EWMA(λ = 0.2)
RSTAT = LocationScaleStatistic(STAT, 1.0, 2.5)
```
