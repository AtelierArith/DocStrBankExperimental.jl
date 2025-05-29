```
ExponentialWeight(λ::Float64)
ExponentialWeight(lookback::Int)
```

指数加重観測。各重みは `λ = 2 / (lookback + 1)` です。

`ExponentialWeight` は通常の仮定 `γ(1) == 1` を満たしません。したがって、一部の統計には暗黙の開始値があります。

```
# 例えば、平均は暗黙の開始値が 0 です。
o = Mean(weight=ExponentialWeight(.1))
fit!(o, 10)
value(o) == 1
```

$$
γ(t) = λ
$$
