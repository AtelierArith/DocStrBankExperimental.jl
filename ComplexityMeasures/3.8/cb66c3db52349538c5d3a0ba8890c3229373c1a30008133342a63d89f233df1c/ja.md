```
BayesianRegularization <: ProbabilitiesEstimator
BayesianRegularization(; a = 1.0)
```

`BayesianRegularization`推定器は、[`probabilities`](@ref)および関連する関数と共に使用され、ベイズ正則化を用いて`m`要素のカウントベースの[`OutcomeSpace`](@ref)の確率を推定します[Hausser2009](@cite)。使用法については、[`ProbabilitiesEstimator`](@ref)を参照してください。

## 結果空間の要件

この推定器は、カウント互換の結果空間でのみ機能します。

## 説明

`BayesianRegularization`推定器は、$k$-番目の結果$\omega_{k}$の確率を次のように推定します。

$$
\omega_{k}^{\text{BayesianRegularization}} = \dfrac{n_k + a_k}{n + A},
$$

ここで、$n$は入力データのサンプル数、$n_k$は結果$\omega_{k}$の観測カウント、$A = \sum_{i=1}^k a_k$です。

## `a`の選択

いくつかの一般的な事前分布の選択肢があり、その一部は[Hausser2009](@citet)にリストされています。これには以下が含まれます。

  * `a == 0`、これは[`RelativeAmount`](@ref)推定器と同等です。
  * `a == 0.5`（ジェフリーズの事前分布）
  * `a == 1`（ベイズ-ラプラスの一様事前分布）

`a`は実数のベクトルとして選択することもできます。その場合、[`allprobabilities_and_outcomes`](@ref)と共に使用する場合は、`length(a) == total_outcomes(o, x)`である必要があります。ここで、`x`は入力データ、`o`は[`OutcomeSpace`](@ref)です。[`probabilities`](@ref)と共に使用する場合は、`length(a)`は*観測された*結果の数と一致しなければなりません（これは[`probabilities_and_outcomes`](@ref)を使用して確認できます）。`a`の選択は確率の推定誤差に大きな影響を与える可能性があり、誤差は`a`の選択とサンプリングシナリオの両方に依存します[Hausser2009](@cite)。

## 仮定

`BayesianRegularization`推定器は、固定された既知の`m`を仮定します。したがって、[`probabilities_and_outcomes`](@ref)および[`allprobabilities_and_outcomes`](@ref)と共に使用すると、入力データで全ての結果が観測されているかどうかに応じて異なる結果が得られます。[`probabilities_and_outcomes`](@ref)の場合、`m`は*観測された*結果の数です。[`allprobabilities_and_outcomes`](@ref)の場合、`m = total_outcomes(o, x)`であり、ここで`o`は[`OutcomeSpace`](@ref)、`x`は入力データです。

!!! note
    [`allprobabilities_and_outcomes`](@ref)と共に使用する場合、観測されていない結果に非ゼロの確率が割り当てられることがあります。これは、例えば[`missing_outcomes`](@ref)を使用する場合に結果に影響を与える可能性があります。


## 例

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps_bayes = probabilities(BayesianRegularization(a = 0.5), OrdinalPatterns{3}(), x)
```

関連情報: [`RelativeAmount`](@ref)、[`Shrinkage`](@ref)。
