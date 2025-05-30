```
pvalue(x::FisherExactTest; tail = :both, method = :central)
```

与えられたフィッシャーの正確検定のp値を計算します。

片側p値は、フィッシャーの非中心超幾何分布 $f_ω(i)$ に基づいています。オッズ比 $ω$ に対して：

$$
    \begin{align*}
        p_ω^{(\text{left})} &=\sum_{i ≤ a} f_ω(i)\\
        p_ω^{(\text{right})} &=\sum_{i ≥ a} f_ω(i)
    \end{align*}
$$

`tail = :both` の場合、`method` の可能な値は次のとおりです：

  * `:central` (デフォルト)：中央区間、すなわちp値は片側p値の最小値の2倍です。
  * `:minlike`：最小尤度区間、すなわちp値は同じ周辺分布を持ち、同じかそれ以下の確率のテーブルをすべて合計することによって計算されます：

    $$
        p_ω = \sum_{f_ω(i)≤ f_ω(a)} f_ω(i)
    $$

# 参考文献

  * Gibbons, J.D., Pratt, J.W., P-values: Interpretation and Methodology, American Statistican, 29(1):20-25, 1975.
  * Fay, M.P., Supplementary material to "Confidence intervals that match Fisher’s exact or Blaker’s exact tests". Biostatistics, Volume 11, Issue 2, 1 April 2010, Pages 373–374, [link](https://doi.org/10.1093/biostatistics/kxp050)
