```
ZBoxRule(low, high)
```

LRP-$zᴮ$-ルール。ピクセル入力の最初の層で一般的に使用されます。

パラメータ `low` と `high` は、入力特徴の下限と上限に設定する必要があります。例えば、生の画像データの場合は `0.0` と `1.0` です。また、入力サイズに一致する2つの配列を提供することも可能です。

# 定義

層出力での関連性 $R^{k+1}$ を層入力での $R^k$ に伝播します。

$$
R_j^k=\sum_i \frac{W_{ij}a_j^k - W_{ij}^{+}l_j - W_{ij}^{-}h_j}
    {\sum_l W_{il}a_l^k+b_i - \left(W_{il}^{+}l_l+b_i^{+}\right) - \left(W_{il}^{-}h_l+b_i^{-}\right)} R_i^{k+1}
$$

# 参考文献

  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
