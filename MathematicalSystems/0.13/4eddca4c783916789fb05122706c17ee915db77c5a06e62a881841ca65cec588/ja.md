```
ConstrainedBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

ドメイン制約のある右辺によって定義された離散時間制御システム：

$$
    x_{k+1} = f(x_k, u_k), \; x_k ∈ \mathcal{X}, \;  u_k ∈ \mathcal{U} \; \forall k.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `X`        – 状態制約
  * `U`        – 入力制約
