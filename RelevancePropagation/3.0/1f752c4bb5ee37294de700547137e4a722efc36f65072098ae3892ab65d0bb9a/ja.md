```
FlatRule()
```

LRP-Flat ルール。すべての重みが1に設定され、すべてのバイアス項が0に設定されている点で、[`WSquareRule`](@ref) に似ています。

# 定義

層の出力での関連性 $R^{k+1}$ を層の入力での $R^k$ に伝播します。

$$
R_j^k = \sum_i\frac{1}{\sum_l 1} R_i^{k+1} = \sum_i\frac{1}{n_i} R_i^{k+1}
$$

ここで、$n_i$ は出力ニューロンのインデックス $i$ に接続されている入力ニューロンの数です。

# 参考文献

  * S. Lapuschkin et al., *Unmasking Clever Hans predictors and assessing what machines really learn*
