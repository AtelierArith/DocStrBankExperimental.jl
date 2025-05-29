```
ConstrainedContinuousIdentitySystem <: AbstractContinuousSystem
```

ドメイン制約を持つ自明な同一連続時間システムの形式：

$$
    x(t)' = 0, \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### フィールド

  * `statedim` – 状態変数の数
  * `X`        – 状態制約
