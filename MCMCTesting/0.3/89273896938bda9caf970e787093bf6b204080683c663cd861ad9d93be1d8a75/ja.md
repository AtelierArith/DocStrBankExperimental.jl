```
TwoSampleTest(n_samples, n_mcmc_steps; n_control, n_treatment, n_mcmc_thin)
```

二標本仮説検定戦略。Gandy & Scott (2021) のアルゴリズム 1。

# 引数

  * `n_samples::Int`: p(θ, y) の結合からのサンプル数。p値を計算するために使用されます。
  * `n_mcmc_steps::Int`: 結合からの初期サンプルに MCMC カーネルが適用される回数。（この値を増やすことでテストのパワーが向上します。）

# キーワード引数

  * `n_control::Int`: 結合からの純粋なサンプル数（対照群）。 （デフォルト: `n_samples`）
  * `n_treatment::Int`: MCMC カーネルからのサンプル数（治療群）。 （デフォルト: `n_samples`）
  * `n_mcmc_thin::Int`: MCMC チェーンに適用される間引きの数。この引数の効果は `n_mcmc_steps` と同じです。

# 戻り値

  * `pvalues`: `statistics` から返される統計量の各次元に対して計算された p 値。

# 要件

このテストには、`model` と `kernel` のために以下の関数が実装されている必要があります：

  * `markovchain_transition`
  * `sample_joint`

# テスト用のキーワード引数

`mcmctest` または `seqmcmctest` を呼び出すとき、このテストには追加のキーワード引数があります：

  * `two_sample_test_pvalue`: p値計算戦略。

デフォルトの戦略は近似二標本コルモゴロフ-スミルノフテストです。二標本仮説検定から単一の p 値を返す任意の関数が機能します。フォーマットは次のとおりです：

```julia
two_sample_test_pvalue(x::AbstractVector, y::AbstractVector)::Real
```
