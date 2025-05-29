```
get_haplotype_transition_matrix(r, θ, α)
```

ハプロタイプにおける隠れマルコフ連鎖の遷移行列を計算します。これは、Sesia et al. の「Gene hunting with hidden Markov model knockoffs」の eq8 の上にある2つの方程式です。

# 入力

`r`: 長さ `p` のベクトル、「再結合率」 `θ`: サイズ `p × K` の行列、`θ[j, k]` は `k` 番目のハプロタイプモチーフにおける SNP `p` のアレルが 1 である確率 `α`: サイズ `p × K` の行列、ハプロタイプモチーフが互いに続く確率。行は 1 に合計されるべきです。

# 出力

`Q`: `K × K` の行列の `p` 次元ベクトル。`Q[:, :, j]` は `j` 番目の遷移行列です。
