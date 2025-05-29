```
PEtabOptimisationResult
```

`calibrate`を用いた単一スタート最適化からのパラメータ推定統計。

参照: [`calibrate`](@ref)

## フィールド

  * `xmin`: 最適化によって見つかった最小化パラメータベクトル。
  * `fmin`: 最適化によって見つかった最小目的値。
  * `x0`: 開始パラメータベクトル。
  * `alg`: 使用されたパラメータ推定アルゴリズム。
  * `niterations`: 最適化のための反復回数。
  * `runtime`: 最適化のための実行時間（秒）。
  * `xtrace`: パラメータベクトルの最適化トレース。`calibrate`に`save_trace = false`が提供された場合は空。
  * `ftrace`: 目的関数の最適化トレース。`calibrate`に`save_trace = false`が提供された場合は空。
  * `converged`: `alg`からの収束フラグ。
  * `original`: `alg`によって返された元の結果構造体。例えば、`alg = IPNewton()`がOptim.jlからの場合、`original`はOptimの返す構造体です。
