```
NoisyConstrainedBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

右辺にドメイン制約を持つ離散時間の外乱影響を受ける制御システムは、次のように定義されます：

$$
    x_{k+1} = f(x_k, u_k), \quad x_k ∈ \mathcal{X}, \quad u_k ∈ \mathcal{U}, \quad w_k ∈ \mathcal{W} \quad \forall k.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `noisedim` – ノイズ変数の数
  * `X`        – 状態制約
  * `U`        – 入力制約
  * `W`        – 外乱セット
