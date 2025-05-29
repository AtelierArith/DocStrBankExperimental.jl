```
NoisyBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

右辺が次の形式の離散時間の外乱影響を受ける制御システム:

$$
    x_{k+1} = f(x_k, u_k) \quad \forall k.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `noisedim` – ノイズ変数の数
