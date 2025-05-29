```
success_probability(n::Integer, t::Integer; p=ones(n)/n, m::Integer=1, r=1, normalize=true)
```

成功確率 `F(t) = P(T ≤ t)` を計算します。ここで、最小のデザイン数 `T` が各モジュールを少なくとも `m` 回見るために必要な回数が `t` より小さい確率を示します。

  * `n`: デザイン空間内のモジュールの数
  * `t`: 成功確率を計算するためのサンプルサイズ/デザインの数
  * `p`: 異なるモジュールの確率または豊富さを持つベクトル
  * `m`: 収集する必要があるモジュールの完全なセットの数
  * `r`: デザインごとのモジュールの数
  * normalize: true の場合、`p` を正規化します

参考文献:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## 例

```julia-repl
julia> n = 100
julia> t = 600
julia> success_probability(n, t; p=ones(n)/n, m=1, r=1, normalize=true)
0.7802171997092149
```
