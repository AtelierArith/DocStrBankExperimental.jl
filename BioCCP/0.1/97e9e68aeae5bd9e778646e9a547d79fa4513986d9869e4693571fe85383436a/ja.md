```
expectation_fraction_collected(n::Integer, t::Integer; p=ones(n)/n, r=1, normalize=true)
```

`t` デザインを収集した後に観測されることが期待されるすべてのモジュールの割合を計算します。

  * `n`: デザイン空間内のモジュールの数
  * `t`: サンプルサイズ/デザインの数
  * `p`: 異なるモジュールの確率または豊富さを持つベクトル
  * `r`: デザインごとのモジュールの数
  * normalize: true の場合、`p` を正規化します

参考文献:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## 例

```julia-repl
julia> n = 100
julia> t = 200
julia> expectation_fraction_collected(n, t; p=ones(n)/n, r=1, normalize=true)
0.8660203251420364
```
