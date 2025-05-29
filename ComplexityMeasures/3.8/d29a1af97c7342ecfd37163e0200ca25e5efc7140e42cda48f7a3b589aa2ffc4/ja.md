```
ProbabilitiesEstimator
```

すべての確率推定器のスーパークラスです。

確率推定器の役割は、（擬似）カウントを確率に変換することです。現在、すべての確率推定器の実装は、既知の基数を持つ*有限*な結果空間を前提としています。したがって、`ProbabilitiesEstimator`は、可能な結果のセットを指定する最初の引数として[`OutcomeSpace`](@ref)を受け入れます。

確率推定器は[`probabilities`](@ref)および[`allprobabilities_and_outcomes`](@ref)と共に使用されます。

## 実装

デフォルトの確率推定器は[`RelativeAmount`](@ref)であり、任意の[`OutcomeSpace`](@ref)と互換性があります。以下の推定器は、カウントベースの結果のみをサポートします。

  * [`Shrinkage`](@ref)。
  * [`BayesianRegularization`](@ref)。
  * [`AddConstant`](@ref)。

## 説明

ComplexityMeasures.jlでは、確率質量関数は、可能な結果のセット$\Omega = \{\omega_1, \omega_2, \ldots, \omega_L \}$（[`OutcomeSpace`](@ref)を指定することによって）を定義し、各結果$\omega_i$に確率$p(\omega_i)$を割り当てることによってデータから推定されます。ここで、$\sum_{i=1}^N p(\omega_i) = 1$（`ProbabilitiesEstimator`を指定することによって）です。
