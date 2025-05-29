```
KruskalWallisTest(groups::AbstractVector{<:Real}...)
```

`groups` $\mathcal{G}$ が同じ分布から来ているという帰無仮説に対して、少なくとも1つのグループが他のグループを確率的に支配しているという対立仮説の下で、クラスカル・ワリス順位和検定を実施します。

クラスカル・ワリス検定は、マン・ホイットニーU検定の2つ以上のグループへの拡張です。

p値は、検定統計量 $H_c=\frac{H}{C}$ の分布に対する $χ^2$ 近似を使用して計算されます：

$$
    \begin{align*}
    H & = \frac{12}{n(n+1)} \sum_{g ∈ \mathcal{G}} \frac{R_g^2}{n_g} - 3(n+1)\\
    C & = 1-\frac{1}{n^3-n}\sum_{t ∈ \mathcal{T}} (t^3-t),
    \end{align*}
$$

ここで、$\mathcal{T}$ は各 tied position での tied values のカウントの集合、$n$ は全グループにわたる観測の総数、$n_g$ と $R_g$ はグループ $g$ の観測数と順位和をそれぞれ表します。詳細については参考文献を参照してください。

実装: [`pvalue`](@ref)

# 参考文献

  * Meyer, J.P, Seaman, M.A., Expanded tables of critical values for the Kruskal-Wallis H statistic. Paper presented at the annual meeting of the American Educational Research Association, San Francisco, April 2006.

# 外部リンク

  * [Kruskal-Wallis test on Wikipedia ](https://en.wikipedia.org/wiki/Kruskal-Wallis_one-way_analysis_of_variance)

```
