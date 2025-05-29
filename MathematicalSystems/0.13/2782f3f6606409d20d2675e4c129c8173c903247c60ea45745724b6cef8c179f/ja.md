```
NoisyLinearControlDiscreteSystem
```

加法的な摂動を持つ連続時間線形制御システムの形式：

$$
    x_{k+1} = A x_k + B u_k + D w_k \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `D` – ノイズ行列
