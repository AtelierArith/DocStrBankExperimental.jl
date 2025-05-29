```
NoisyConstrainedLinearContinuousSystem
```

加法的な外乱と次の形式の領域制約を持つ連続時間線形システム：

$$
    x(t)' = A x(t) + D w(t), \; x(t) ∈ \mathcal{X}, \; w(t) ∈ \mathcal{W} \; \forall t.
$$

### フィールド

  * `A` – 状態行列
  * `D` – ノイズ行列
  * `X` – 状態制約
  * `W` – 外乱集合
