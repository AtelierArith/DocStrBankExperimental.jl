```
prob_occurrence_module(pᵢ, t::Integer, r, k::Integer)
```

特定のモジュールがモジュール確率 `pᵢ` で `t` デザインを収集した後に `k` 回発生する確率を計算します。

個々のモジュールのサンプリングプロセスは独立したポアソンプロセスであると仮定されています。

  * `pᵢ`: モジュール確率
  * `t`: サンプルサイズ/デザインの数
  * `k`: 発生回数

参考文献:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## 例

```julia-repl
julia> pᵢ = 0.005
julia> t = 500
julia> k = 2
julia> r = 1
julia> prob_occurrence_module(pᵢ, t, r, k)
0.25651562069968376
```
