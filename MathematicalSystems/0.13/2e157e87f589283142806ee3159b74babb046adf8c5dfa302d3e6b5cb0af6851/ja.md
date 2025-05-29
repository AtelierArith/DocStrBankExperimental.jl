```
NoisyAffineControlContinuousSystem
```

加法的な摂動を持つ連続時間アフィン制御システムの形式：

$$
    x(t)' = A x(t) + B u(t) + c + D w(t) \; \forall t.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `D` – ノイズ行列
