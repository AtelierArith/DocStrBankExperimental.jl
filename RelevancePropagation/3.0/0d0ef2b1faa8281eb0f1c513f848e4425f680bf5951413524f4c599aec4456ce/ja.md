```
GammaRule([gamma=0.25])
```

LRP-$γ$ ルール。下層で一般的に使用されます。

# 定義

層出力での関連性 $R^{k+1}$ を層入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac{(W_{ij}+\gamma W_{ij}^+)a_j^k}
    {\sum_l(W_{il}+\gamma W_{il}^+)a_l^k+(b_i+\gamma b_i^+)} R_i^{k+1}
$$

# オプション引数

  * `gamma`: 追加の正の重みのためのオプションの乗数で、デフォルトは `0.25` です。

# 参考文献

  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
