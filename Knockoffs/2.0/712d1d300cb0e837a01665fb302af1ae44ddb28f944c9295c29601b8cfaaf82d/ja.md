```
ghost_knockoffs(Zscores, D, Σinv; [m=1])
```

Zスコアのリスト（GWAS要約統計）からゴーストノックオフを生成します。

# 入力

  * `Zscores`: zスコア統計のリスト
  * `D`: ノックオフ問題を解くことで得られた行列で、`(m+1)/m*Σ - D ⪰ 0` を満たす
  * `Σinv`: 共分散行列の逆行列

# オプション入力

  * `m`: ノックオフの数

# 参考文献

He, Z., Liu, L., Belloy, M. E., Le Guen, Y., Sossin, A., Liu, X., ... & Ionita-Laza, I. (2021).  Summary statistics knockoff inference empowers identification of putative causal variants in genome-wide association studies. 
