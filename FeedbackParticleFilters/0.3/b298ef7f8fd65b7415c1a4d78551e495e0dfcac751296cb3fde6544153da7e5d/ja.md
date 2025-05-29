```
DiffusionStateModel(f::Function, g::Function, init)
```

拡散過程の隠れ状態モデル $dX_t = f(X_t)dt + g(X_t)dW_t$ を返します。ここで、$f$ は `drift_function`、$g$ は `observation_function`、$X_t$ は時刻 $t$ における $n$ 次元の隠れ状態、$W_t$ は $m$ 次元のブラウン運動過程です。

引数 `init` はプロセスの初期条件を表し、次のいずれかです。

  * 固定（決定論的）初期条件のための長さ `n` のベクトル
  * ランダム初期条件のための `Distributions.Sampleable` 型
