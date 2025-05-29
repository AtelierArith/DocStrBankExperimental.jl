```
ConstrainedAffineControlMap
```

状態と入力の制約を持つアフィン制御マップ

$$
    (x, u) ↦ Ax + Bu + c, x ∈ \mathcal{X}, u ∈ \mathcal{U}.
$$

### フィールド

  * `A` – 行列
  * `B` – 行列
  * `c` – ベクトル
  * `X` – 状態制約
  * `U` – 入力制約
