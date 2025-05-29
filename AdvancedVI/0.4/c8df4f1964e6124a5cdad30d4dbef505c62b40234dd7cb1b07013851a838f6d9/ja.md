```
RepGradELBO(n_samples; kwargs...)
```

再パラメータ化勾配定式を用いた証拠下限目的[^TL2014][^RMW2014][^KW2014]。これは、次の定式を通じて証拠下限（ELBO）を計算します：

$$
\begin{aligned}
\mathrm{ELBO}\left(\lambda\right)
&\triangleq
\mathbb{E}_{z \sim q_{\lambda}}\left[
  \log \pi\left(z\right)
\right]
+ \mathbb{H}\left(q_{\lambda}\right),
\end{aligned}
$$

# 引数

  * `n_samples::Int`: ELBOを推定するために使用されるモンテカルロサンプルの数。

# キーワード引数

  * `entropy`: エントロピー項の推定器。 (タイプ `<: AbstractEntropyEstimator`; デフォルト: `ClosedFormEntropy()`)

# 要件

  * 変分近似 $q_{\lambda}$ は `rand` を実装している必要があります。
  * 対象分布と変分近似は同じサポートを持っている必要があります。
  * 対象の `logdensity(prob, x)` は、選択されたADバックエンドに対して `x` に関して微分可能でなければなりません。

オプションに応じて、$q_{\lambda}$ に対する追加の要件が適用される場合があります。
