```
NoisyConstrainedLinearDiscreteSystem
```

加法的な外乱と次の形式の領域制約を持つ離散時間線形システム：

$$
    x_{k+1} = A x_k + D w_k, \; x_k ∈ \mathcal{X}, \; w(t) ∈ \mathcal{W} \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `D` – ノイズ行列
  * `X` – 状態制約
  * `W` – 外乱集合
