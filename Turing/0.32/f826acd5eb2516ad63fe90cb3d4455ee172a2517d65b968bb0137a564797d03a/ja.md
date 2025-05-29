```
OrderedLogistic(η, c::AbstractVector)
```

*順序ロジスティック分布*は、実数値パラメータ`η`とカットポイント`c`を持ち、確率質量関数は次のようになります。

$$
P(X = k) = \begin{cases}
    1 - \text{logistic}(\eta - c_1) & \text{if } k = 1, \\
    \text{logistic}(\eta - c_{k-1}) - \text{logistic}(\eta - c_k) & \text{if } 1 < k < K, \\
    \text{logistic}(\eta - c_{K-1}) & \text{if } k = K,
\end{cases}
$$

ここで、`K = length(c) + 1`です。
