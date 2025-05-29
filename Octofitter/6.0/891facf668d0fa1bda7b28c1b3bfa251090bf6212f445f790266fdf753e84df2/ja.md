```
ObsPriorAstromONeil2019(astrometry_likelihood, period_prior)
```

与えられた天体測定の尤度（`PlanetRelAstromLikelihood`）に対して、K. O'Neil 2019の「不完全な軌道のための軌道推定の改善：ブラックホールから惑星への応用に向けた新しいアプローチによる事前分布」の「観測可能に基づく事前分布」を適用します。

この事前補正は、すべてのキャンベル軌道パラメータに対して一様事前分布を供給し、期間に対して一様事前分布（半長軸ではなく）を供給した場合にのみ正しいです。この期間の事前分布はフィットに大きな影響を与え、その範囲に関する推奨は元の論文では発表されていません。

## 例

```julia
astrom_like = PlanetRelAstromLikelihood(astrom_table)

# 一様キャンベル事前分布の上に観測可能に基づく事前分布を適用します：
obs_prior = ObsPriorAstromONeil2019(astrom_like)

# 天体測定の尤度オブジェクトは最初のパラメータとして渡されます
# 観測可能に基づく事前分布は観測
# エポックに依存します。

@planet b Visual{KepOrbit} begin
    # 半長軸に対する事前分布の代わりに
    # a ~ Uniform(0.001, 10000)

    # 期間に対する事前分布を設定します：
	P ~ Uniform(0.001, 2000) # 年
    a = cbrt(system.M * b.P^2)

    # 傾斜に対するサイン事前分布を維持します
    i ~ Sine()

    # 残りは一様です
    e ~ Uniform(0.0, 1.0)
    ω ~ UniformCircular()
    Ω ~ UniformCircular()
    τ ~ UniformCircular(1.0)
end astrom_like obs_prior
```
