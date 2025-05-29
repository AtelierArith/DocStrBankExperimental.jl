```
is_choi_matrix(
    Λ :: AbstractMatrix,
    dims :: Vector{Int};
    atol=ATOL :: Float
) :: Bool
```

行列 `Λ` が量子チャネルの Choi 演算子表現である場合、`true` を返します。

`Λ` に対する要件は ([https://arxiv.org/abs/1111.6950](https://arxiv.org/abs/1111.6950)):

  * エルミートである、$\Lambda = \Lambda^{\dagger}$。
  * トレース保存である、$\text{Tr}_B[\Lambda^{AB}]=\mathbb{I}_A$。
  * 完全正である、$\Lambda \geq 0$。
