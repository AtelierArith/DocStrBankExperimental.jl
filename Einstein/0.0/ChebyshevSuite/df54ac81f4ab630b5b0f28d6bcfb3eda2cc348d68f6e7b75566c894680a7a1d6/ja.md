```
cheb_series_filter_weights_exp([TF=Float64], n::Integer, a::Integer, p::Integer) where {TF<:AbstractFloat}
```

チェビシェフ級数の指数フィルタ重みを計算します [Szilagyi:2009qz](@cite)。

$$
w_k = e^{-\alpha\left(k / n\right)^{2 p}}, \quad k = 0, \ldots, n-1
$$

# 引数

  * `TF`: 浮動小数点精度の型パラメータ
  * `n`: グリッドポイントの数
  * `α`: フィルタ強度パラメータ
  * `p`: フィルタの次数

# 例

  * $$
    \alpha = 36
    $$

    および $p = 32$ は弱いフィルタ [Szilagyi:2009qz, Hilditch:2015aba](@cite)
  * $$
    \alpha = 40
    $$

    および $p = 8$ は強いフィルタ [justin*ripley*2023_8215577](@cite)

```
