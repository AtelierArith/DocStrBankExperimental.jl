```
ZPlusRule()
```

LRP-$z⁺$ ルール。下層で一般的に使用されます。

`AlphaBetaRule(1.0f0, 0.0f0)` と同等ですが、わずかに高速です。詳細は [`AlphaBetaRule`](@ref) を参照してください。

# 定義

層の出力での関連性 $R^{k+1}$ を層の入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac{\left(W_{ij}a_j^k\right)^+}{\sum_l\left(W_{il}a_l^k+b_i\right)^+} R_i^{k+1}
$$

# 参考文献

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
  * G. Montavon et al., *Explaining Nonlinear Classification Decisions with Deep Taylor Decomposition*
