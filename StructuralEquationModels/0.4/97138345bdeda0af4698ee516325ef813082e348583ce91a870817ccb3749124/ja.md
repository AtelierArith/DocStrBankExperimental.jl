```
SemFit
```

適合した構造方程式モデル。

# インターフェース

  * `minimum(::SemFit)` -> 最小目的値
  * `solution(::SemFit)` -> パラメータ推定
  * `start_val(::SemFit)` -> 開始値
  * `model(::SemFit)`
  * `optimization_result(::SemFit)`
  * `optimizer(::SemFit)` -> 最適化アルゴリズム
  * `n_iterations(::SemFit)` -> 繰り返し回数
  * `convergence(::SemFit)` -> 収束特性
