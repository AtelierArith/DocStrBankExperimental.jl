```
FlignerKilleenTest(groups)
FlignerKilleenTest(groups::AbstractVector{<:Real}...)
```

`groups`が等しい分散を持つという帰無仮説のFligner-Killeen中央値検定を実行します。これは分散の均一性に対する検定です。

この検定は正規性からの逸脱に対して最も堅牢です。参考文献を参照してください。これは、中心化されたサンプルの絶対値の順位を使用する$k$サンプル単純線形順位法です。

$$
a_{N,i} = \Phi^{-1}(1/2 + (i/2(N+1)))
$$

ここで実装されているバージョンは、各サンプルで中央値中心化を使用します。

実装: [`pvalue`](@ref)

# 参考文献

  * Conover, W. J., Johnson, M. E., Johnson, M. M., 分散の均一性に関する検定の比較研究、外洋棚入札データへの応用。Technometrics, 23, 351–361, 1980

# 外部リンク

  * [Fligner-Killeen test on Statistical Analysis Handbook ](https://www.statsref.com/HTML/index.html?fligner-killeen_test.html)

```
