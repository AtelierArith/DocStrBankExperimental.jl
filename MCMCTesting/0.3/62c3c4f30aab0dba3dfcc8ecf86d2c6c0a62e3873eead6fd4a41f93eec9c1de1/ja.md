```
TwoSampleTest(n_samples, n_mcmc_steps; n_control, n_treatment, n_mcmc_thin)
```

追加のギブスサンプリングステップを持つ二標本仮説検定戦略。Gandy & Scott 2021のアルゴリズム1の修正版で、検定の力を高めます。

# 引数

  * `n_samples::Int`: p(θ, y)の結合からのサンプル数で、p値を計算するために使用されます。
  * `n_mcmc_steps::Int`: 結合からの初期サンプルにMCMCカーネルが適用される回数。（この値を増やすことで検定の力が向上します。）

# キーワード引数

  * `n_control::Int`: 結合からの純粋なサンプル数（対照群）。（デフォルト: `n_samples`）
  * `n_treatment::Int`: MCMCカーネルからのサンプル数（治療群）。（デフォルト: `n_samples`）
  * `n_mcmc_thin::Int`: MCMCチェーンに適用される間引きの数。この引数の効果は`n_mcmc_steps`と同じです。

# 戻り値

  * `pvalues`: `statistics`から返される統計量の各次元に対して計算されたp値。

# 要件

このテストには、`model`および`kernel`のために以下の関数が実装されている必要があります：

  * `markovchain_transition`
  * `sample_joint`
  * `sample_predictive`

# テスト用のキーワード引数

`mcmctest`または`seqmcmctest`を呼び出すとき、このテストには追加のキーワード引数があります：

  * `two_sample_test_pvalue`: p値計算戦略。

デフォルトの戦略は近似二標本コルモゴロフ-スミルノフテストです。二つのサンプル群に対してp値を返す任意の関数が機能します。フォーマットは次の通りです：

```julia
two_sample_test_pvalue(x::AbstractVector, y::AbstractVector)::Real
```

# 参考文献
