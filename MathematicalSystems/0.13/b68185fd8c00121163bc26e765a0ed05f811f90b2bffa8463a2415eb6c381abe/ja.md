```
NoisyConstrainedLinearControlDiscreteSystem
```

加法的な外乱と次の形式の領域制約を持つ連続時間線形制御システム：

$$
    x_{k+1} = A x_k + B u_k + D w_k, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U}, \; w_k ∈ \mathcal{W} \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `D` – ノイズ行列
  * `X` – 状態制約
  * `U` – 入力制約
  * `W` – 外乱集合
