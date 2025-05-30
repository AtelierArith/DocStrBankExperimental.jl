```
MAP
```

元のPrecision@$N$は固定長の推薦リスト$I_N(u)$に対してスコアを提供しますが、平均適合率（MAP）は、すべての推薦サイズ1から$|\mathcal{I}|$までのスコアの平均を計算します。MAPは、$I(u)$の$n$-番目のアイテム$i_n$に対する指示関数を用いて次のように定式化されます：

$$
\mathrm{MAP} = \frac{1}{|\mathcal{I}^+_u|} \sum_{n = 1}^{|\mathcal{I}|} \mathrm{Precision@}n \cdot  \mathbb{1}_{\mathcal{I}^+_u}(i_n).
$$

注意すべきは、MAPはPrecision@$1$、Precision@$2$、$\dots$、Precision@$|\mathcal{I}|$の合計の単純な平均ではなく、より高いランクの真のポジティブがより良いMAPをもたらすということです。

```
measure(
    metric::MAP,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
