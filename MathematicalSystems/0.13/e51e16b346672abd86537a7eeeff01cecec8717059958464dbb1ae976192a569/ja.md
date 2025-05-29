```
NoisyConstrainedAffineControlDiscreteSystem
```

加法的な摂動と次の形式の領域制約を持つ連続時間アフィン制御システム：

$$
    x_{k+1} = A x_k + B u_k + c + D w_k, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U}, \; w_k ∈ \mathcal{W} \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `D` – ノイズ行列
  * `X` – 状態制約
  * `U` – 入力制約
  * `W` – 摂動集合
