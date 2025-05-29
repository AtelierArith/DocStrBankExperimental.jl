```
DPMM(comp_mu::Real,
     comp_lambda::Real,
     comp_alpha::Real,
     comp_beta::Real,
     dirichlet_alpha::Real;
     comp_birth_thres=1e-2,
     comp_death_thres=1e-2,
     n_comp_max=10)
```

オンライン単変量ディリクレ過程ガウス混合モデルアルゴリズム。

# 数学的説明

モデルは次のように記述されます。

```
G ~ DP(dirchlet_alpha, Normal-Gamma)
(μₖ, τₖ) ~ G
x ~ N(μ, 1/sqrt(τ))
```

ここで、基準測度は次のように定義されます。

```
τₖ ~ Gamma(comp_alpha, 1/comp_beta)
μₖ ~ N(comp_mu, 1/sqrt(comp_lambda*τₖ)).
```

変分分布は、次のように定義される平均場ファミリーです。

```
q(μₖ | τₖ; mₖ, lₖ) q(τₖ; aₖ, bₖ) = N(μₖ; mₖ, 1/(lₖ*τₖ)) Gamma(τₖ; aₖ, 1/bₖ).
```

モデルは非パラメトリックであるため、混合成分は出生閾値 `comp_birth_thres` に応じて追加され（高いほど出生頻度が低くなる）、既存の成分は死亡閾値 `comp_death_thres` に応じて剪定されます。

# ハイパーパラメータ

DPMMはそのハイパーパラメータに非常に敏感です。したがって、フィッティング結果を監視し、ハイパーパラメータを適宜調整することが重要です。各ハイパーパラメータの意味は次のとおりです。

  * `comp_mu`: 成分の事前平均
  * `comp_lambda`: 成分の事前精度。これは各成分のスケールに対する成分の分散に影響します。（小さいほど分散が大きくなる。）(`comp_lambda` > 0)
  * `comp_alpha`: 各成分のスケール（分散の逆数）のガンマ形状パラメータ。(`comp_alpha` > 0)
  * `comp_beta`: 各成分のスケール（分散の逆数）のガンマスケールパラメータ。(`comp_beta` > 0)
  * `dirichlet_alpha`: 新しく追加された成分の初期重み。大きな値はより多くの成分が作成されることを意味します。(`dirichlet_alpha` > 0)
  * `comp_birth_thres`: 新しい成分を追加するための閾値（`dirichlet_alpha` に強く影響される）
  * `comp_death_thres`: 既存の成分を剪定（または削除）するための閾値。

成分のハイパーパラメータを設定するための機械的手順は、まず `comp_alpha > 2` を設定することです。これにより、分散が有限であることが保証されます。次に、ガンマ分布が `1/τₖ` の期待範囲にほとんどの確率密度を集中させるように `comp_beta` を解決します。最後に、μₖの周辺密度が学生t分布であるように `comp_lambda` を解決します。

```
p(μₖ | λ₀, α₀, β₀)
    = ∫ p(μₖ | τₖ, μ₀, λ₀) p(τₖ | α₀, β₀) dτₖ
    = ∫ N(μₖ; μ₀, 1/sqrt(λ₀*τₖ)) Gamma(τₖ; αₖ, βₖ) dτₖ
    = TDist( 2*α₀, μ₀, sqrt(β₀/(λ₀*α₀)),
```

成分平均の期待範囲に確率密度が集中します。

以下は、上記の事前引き出し手順を実装したものです。

```
using Roots

prob_τₖ = 0.8
τₖ_max  = 0.5
μ₀      = 0.0
α₀      = 2.1
prob_μₖ = 0.8
μₖ_min  = -2
μₖ_max  = 2

β₀ = find_zero(β₀ -> cdf(InverseGamma(α₀, β₀), τₖ_max) - prob_τₖ, (1e-4, Inf))
λ₀ = find_zero(λ₀ -> begin
    p_μ = TDist(2*α₀)*sqrt(β₀/(λ₀*α₀)) + μ₀
    cdf(p_μ, μₖ_max) - cdf(p_μ, μₖ_min) - prob_τₖ
end, (1e-4, 1e+2))
```

`prob_*` は、望ましい範囲における密度の量を設定します。`τₖ_max`、`μₖ_min`、`μₖ_max` は各パラメータの期待範囲です。`1 - prob_*` の密度を尾部に残すため、これらはソフト制約です。

残念ながら、`dirichlet_alpha`、`comp_birth_thres`、`comp_death_thres` は試行錯誤を通じてのみ調整できます。ただし、`dirichlet_alpha` は、望ましい成分数に応じて0.5〜1e-2に設定するのが最適です。

# 例

```
n    = 1024
μ    = 0.0
λ    = 0.1
α    = 2.1
β    = 0.5
α_dp = 1.0
o    = DPMM(μ, λ, α, β, α_dp; comp_birth_thres=0.5,
            comp_death_thres=1e-2, n_comp_max=10) 
p = MixtureModel([ Normal(-2.0, 0.5), Normal(3.0, 1.0) ], [0.7, 0.3])
o = fit!(o, rand(p, 1000))
```
