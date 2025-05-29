```
NoisyAffineControlDiscreteSystem
```

加法的な摂動を持つ連続時間アフィン制御システムの形式：

$$
    x_{k+1} = A x_k + B u_k + c + D w_k \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `D` – ノイズ行列
