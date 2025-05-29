```
EllipticalSet <: CenteredAmbiguitySet{T,D}
```

$$
\left\{ \mu \; \middle| \begin{array}{ll}
s.t.  \quad \sqrt{(\hat{r} - \mu) ' \Sigma^{-1} (\hat{r} - \mu)} \leq \delta \\
\end{array}
\right\} \\
$$

属性:

  * `d::Sampleable{Multivariate, Continous}`: 不確実な平均を持つ親分布
  * `Δ::Array{Float64,1}`: 平均周辺の一様な不確実性。(デフォルト: 0.025)

参考文献:

  * Ben-Tal, A. e Nemirovski, A. (2000). 不確実なデータで汚染された線形計画問題のロバスト解. 数理最適化, 88(3):411–424.
