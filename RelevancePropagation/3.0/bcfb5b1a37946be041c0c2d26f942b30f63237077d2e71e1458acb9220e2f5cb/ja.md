```
ZeroRule()
```

LRP-$0$ ルール。上層で一般的に使用されます。

# 定義

出力層の関連性 $R^{k+1}$ を入力層の $R^k$ に伝播します。

$$
R_j^k = \sum_i \frac{W_{ij}a_j^k}{\sum_l W_{il}a_l^k+b_i} R_i^{k+1}
$$

# 参考文献

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
