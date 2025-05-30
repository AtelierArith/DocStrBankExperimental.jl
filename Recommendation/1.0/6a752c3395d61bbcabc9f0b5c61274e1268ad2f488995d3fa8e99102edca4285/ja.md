```
逆数ランク
```

最初の真の陽性にのみ関心がある場合、逆数ランク（RR）は推薦リストを定量的に評価するための合理的な選択となる可能性があります。$n_{\mathrm{tp}} \in \left[ 1, |\mathcal{I}| \right]$は$I(u)$における最初の真の陽性の位置を示し、RRは単にその逆数を返します：

$$
  \mathrm{RR} = \frac{1}{n_{\mathrm{tp}}}.
$$

RRは、$\mathcal{I}^+_u$が空である場合に限りゼロになります。

```
measure(
    metric::ReciprocalRank,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
