```
GeneralizedGammaRule([gamma=0.25])
```

一般化LRP-$γ$ルール。`leakyrelu`活性化関数を持つ層で使用できます。

# 定義

層出力での関連性 $R^{k+1}$ を層入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac
    {(W_{ij}+\gamma W_{ij}^+)a_j^+ +(W_{ij}+\gamma W_{ij}^-)a_j^-}
    {\sum_l(W_{il}+\gamma W_{il}^+)a_j^+ +(W_{il}+\gamma W_{il}^-)a_j^- +(b_i+\gamma b_i^+)}
I(z_k>0) \cdot R^{k+1}_i
+\sum_i\frac
    {(W_{ij}+\gamma W_{ij}^-)a_j^+ +(W_{ij}+\gamma W_{ij}^+)a_j^-}
    {\sum_l(W_{il}+\gamma W_{il}^-)a_j^+ +(W_{il}+\gamma W_{il}^+)a_j^- +(b_i+\gamma b_i^-)}
I(z_k<0) \cdot R^{k+1}_i
$$

# オプション引数

  * `gamma`: 追加された正の重みのためのオプショナルな乗数で、デフォルトは `0.25` です。

# 参考文献

  * L. Andéol et al., *Learning Domain Invariant Representations by Joint Wasserstein Distance Minimization*
