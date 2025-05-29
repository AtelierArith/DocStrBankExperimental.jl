```
LinearRightConstant(bandwidth)
```

線形右定数 [コンポーネント損失](@ref AbstractComponentLoss) 因子回転基準。損失関数は次の通りです。

$$
h(\lambda) = \begin{cases}
    (\frac{\lambda}{b})^2&\text{if } |\lambda| \leq b \\
    1 &\text{if } |\lambda| > b,
\end{cases}
$$

ここで、$b$ は *バンド幅* パラメータです。
