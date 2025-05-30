```
ConstrainedDiscreteIdentitySystem <: AbstractDiscreteSystem
```

ドメイン制約を持つ自明な単位離散時間システムの形式：

$$
    x_{k+1} = x_k, \; x_k ∈ \mathcal{X} \; \forall k.
$$

### フィールド

  * `statedim` – 状態変数の数
  * `X`        – 状態制約
