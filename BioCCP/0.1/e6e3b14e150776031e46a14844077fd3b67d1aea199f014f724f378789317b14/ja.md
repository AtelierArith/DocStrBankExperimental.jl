```
expectation_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
```

各モジュールを少なくとも `m` 回観察するために必要な設計の期待最小数 `E[T]` を計算します。

  * `n`: 設計空間内のモジュールの数
  * `p`: 異なるモジュールの確率または豊富さを持つベクトル
  * `m`: サンプリングされた設計セット内で各モジュールが観察される回数
  * `r`: 設計ごとのモジュールの数
  * normalize: true の場合、`p` を正規化します

参考文献:

  * Doumas, A. V., & Papanicolaou, V. G. (2016). The coupon collector’s problem revisited:   generalizing the double Dixie cup problem of Newman and Shepp. ESAIM: Probability   and Statistics, 20, 367-399.
  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of   engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## 例

```julia-repl
julia> n = 100
julia> expectation_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
518
```
