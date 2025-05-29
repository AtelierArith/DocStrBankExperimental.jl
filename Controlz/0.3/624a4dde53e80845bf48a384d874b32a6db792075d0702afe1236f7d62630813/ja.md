```
K = zero_frequency_gain(tf)
```

伝達関数 $g(s)$ の（符号付き）ゼロ周波数ゲインを計算します。これは次のように定義されます：

$$
K := \lim_{s\rightarrow 0} G(s)
$$

ゼロ周波数ゲインは「ステップ入力に対する出力の定常状態値の比を表します」 [source](http://www.cds.caltech.edu/~murray/books/AM05/pdf/am06-xferfcns_16Sep06.pdf)

# 例

```jldoctest
g = 5 / (3 * s + 1)
K = zero_frequency_gain(g)
# 出力
5.0
```

# 引数

  * `tf::TransferFunction`: 伝達関数

# 戻り値

  * `K::Float64`: 伝達関数のゼロ周波数ゲイン
