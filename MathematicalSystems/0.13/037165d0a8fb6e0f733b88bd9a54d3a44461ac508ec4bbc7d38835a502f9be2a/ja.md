```
NoisyBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

右辺が次の形式の連続時間の外乱影響を受ける制御システム:

$$
    x(t)' = f(x(t), u(t), w(t)) \; \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `noisedim` – ノイズ変数の数
