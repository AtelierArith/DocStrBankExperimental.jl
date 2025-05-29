```
EpsilonRule([epsilon=1.0e-6])
```

LRP-$ϵ$ ルール。中間層で一般的に使用されます。

# 定義

層出力での関連性 $R^{k+1}$ を層入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac{W_{ij}a_j^k}{\epsilon +\sum_{l}W_{il}a_l^k+b_i} R_i^{k+1}
$$

# オプション引数

  * `epsilon`: オプションの安定化パラメータ、デフォルトは `1.0e-6` です。

# 参考文献

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
