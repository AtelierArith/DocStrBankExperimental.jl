```
AlphaBetaRule([alpha=2.0, beta=1.0])
```

LRP-$αβ$ ルール。パラメータ `alpha` と `beta` に従って、正の寄与と負の寄与に重みを付けます。差 $α-β$ は1に等しくなければなりません。一般的に下層で使用されます。

# 定義

層出力での関連性 $R^{k+1}$ を層入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\left(
    \alpha\frac{\left(W_{ij}a_j^k\right)^+}{\sum_l\left(W_{il}a_l^k+b_i\right)^+}
    -\beta\frac{\left(W_{ij}a_j^k\right)^-}{\sum_l\left(W_{il}a_l^k+b_i\right)^-}
\right) R_i^{k+1}
$$

# オプション引数

  * `alpha`: 正の出力項の乗数、デフォルトは `2.0`。
  * `beta`: 負の出力項の乗数、デフォルトは `1.0`。

# 参考文献

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
