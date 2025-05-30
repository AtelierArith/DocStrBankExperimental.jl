```
ConstrainedBlackBoxDiscreteSystem <: AbstractDiscreteSystem
```

ドメイン制約のある右辺によって定義された離散時間システムの形式：

$$
    x_{k+1} = f(x_k), \; x_k ∈ \mathcal{X} \; \forall k.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `X`        – 状態制約
