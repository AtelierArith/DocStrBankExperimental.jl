```
NoisyConstrainedBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

右辺が次の形式のドメイン制約を持つ連続時間の外乱影響を受ける制御システム:

$$
    x(t)' = f(x(t), u(t), w(t)), \quad x(t) ∈ \mathcal{X}, \quad u(t) ∈ \mathcal{U}, \quad w(t) ∈ \mathcal{W} \quad \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `noisedim` – ノイズ変数の数
  * `X`        – 状態制約
  * `U`        – 入力制約
  * `W`        – 外乱セット
