```
MultivariateMoments.low_rank_ldlt(Q::AbstractMatrix, dec::LowRankLDLTAlgorithm, ranktol)
```

$$
Q
$$

が$r$ランクの$n \times n$の半正定値行列であるとき、$Q = U^\top U$となる$r \times n$行列$U$を返します。$Q$のランクは、$\sigma_1$が最大の特異値であるとき、`ranktol`${} \cdot \sigma_1$より大きい特異値の数です。
