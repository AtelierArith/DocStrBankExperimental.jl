```
normalize(s, n; <キーワード引数>)
```

正規化。

# 引数

  * `s::AbstractVector`
  * `n::Real=1.0`
  * `method::Symbol`:

      * `:zscore`: zスコアによる
      * `:minmax`: [-1, +1]の範囲で
      * `:log`: 対数変換を使用
      * `:log10`: log10変換を使用
      * `:neglog`: -log変換を使用
      * `:neglog10`: -log10変換を使用
      * `:neg`: [-∞, 0]の範囲で
      * `:pos`: [0, +∞]の範囲で
      * `:perc`: パーセンテージで
      * `:gauss`: ガウス分布に
      * `:invroot`: 逆平方根に: 1/sqrt(x)
      * `:n`: [0, n]の範囲で、デフォルトは[0, 1]
      * `:softmax`: ソフトマックス関数を使用: exp(x_i) / sum(exp(x))
      * `:sigmoid`: シグモイド関数を使用: 1 /  1 + exp(-x_i)
      * `:mad`: MADによる
      * `:rank`: タイドランクを使用
      * `:none`

# 戻り値

  * `normalized::AbstractVector`

```
