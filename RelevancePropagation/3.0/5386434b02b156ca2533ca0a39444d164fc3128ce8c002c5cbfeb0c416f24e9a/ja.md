```
WSquareRule()
```

LRP-$w²$ ルール。値が無制限のときに最初の層で一般的に使用されます。

# 定義

層の出力での関連性 $R^{k+1}$ を層の入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac{W_{ij}^2}{\sum_l W_{il}^2} R_i^{k+1}
$$

# 参考文献

  * G. Montavon et al., *Explaining Nonlinear Classification Decisions with Deep Taylor Decomposition*
