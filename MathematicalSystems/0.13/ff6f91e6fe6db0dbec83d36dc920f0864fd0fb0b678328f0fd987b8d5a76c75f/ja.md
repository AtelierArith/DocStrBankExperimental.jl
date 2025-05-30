```
NoisyConstrainedAffineControlContinuousSystem
```

加法的な摂動と次の形式のドメイン制約を持つ連続時間アフィン制御システム：

$$
    x(t)' = A x(t) + B u(t) + c + D w(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U}, \; w(t) ∈ \mathcal{W} \; \forall t.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `D` – ノイズ行列
  * `X` – 状態制約
  * `U` – 入力制約
  * `W` – 摂動集合
