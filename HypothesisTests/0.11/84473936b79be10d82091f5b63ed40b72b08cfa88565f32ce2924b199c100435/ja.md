```
LeveneTest(groups; scorediff=abs, statistic=mean)
LeveneTest(groups::AbstractVector{<:Real}...; scorediff=abs, statistic=mean)
```

`groups` の分散が等しいという仮説の Levene テストを実行します。デフォルトでは、各 `groups` の中心化に平均 `statistic` が使用されますが、他の統計量も受け入れられます：中央値または切断平均、詳細は [`BrownForsytheTest`](@ref) を参照してください。デフォルトでは、スコア差の絶対値 `scorediff` が使用されますが、他の関数も受け入れられます：x² または √|x|。

テスト統計量 $W$ は $F$ 統計量に相当し、次のように定義されます：

$$
W = \frac{(N-k)}{(k-1)} \cdot \frac{\sum_{i=1}^k N_i (Z_{i\cdot}-Z_{\cdot\cdot})^2}
    {\sum_{i=1}^k \sum_{j=1}^{N_i} (Z_{ij}-Z_{i\cdot})^2},
$$

ここで

  * $$
    k
    $$

    はサンプルケースが属する異なるグループの数です。
  * $$
    N_i
    $$

    は $i$ 番目のグループのケースの数です。
  * $$
    N
    $$

    はすべてのグループのケースの総数です。
  * $$
    Y_{ij}
    $$

    は $i$ 番目のグループからの $j$ 番目のケースの測定変数の値です。
  * $$
    Z_{ij} = |Y_{ij} - \bar{Y}_{i\cdot}|
    $$

    、$\bar{Y}_{i\cdot}$ は $i$ 番目のグループの平均です。
  * $$
    Z_{i\cdot} = \frac{1}{N_i} \sum_{j=1}^{N_i} Z_{ij}
    $$

    はグループ $i$ の $Z_{ij}$ の平均です。
  * $$
    Z_{\cdot\cdot} = \frac{1}{N} \sum_{i=1}^k \sum_{j=1}^{N_i} Z_{ij}
    $$

    はすべての $Z_{ij}$ の平均です。

テスト統計量 $W$ は、自由度 $k-1$ および $N-k$ の $F$ 分布に近似されます。

実装： [`pvalue`](@ref)

# 参考文献

  * Levene, Howard, "Robust tests for equality of variances".  In Ingram Olkin; Harold Hotelling; et al. (eds.).  Contributions to Probability and Statistics: Essays in Honor of Harold Hotelling.  Stanford University Press. pp. 278–292, 1960

# 外部リンク

  * [Levene's test on Wikipedia ](https://en.wikipedia.org/wiki/Levene%27s_test)

```
