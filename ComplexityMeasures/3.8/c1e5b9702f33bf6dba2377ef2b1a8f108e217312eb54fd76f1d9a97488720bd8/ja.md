```
DiscreteInfoEstimator
```

すべての離散情報測定推定器のスーパークラスであり、[`ProbabilitiesEstimator`](@ref)と組み合わせて[`information`](@ref)や関連関数への入力として使用されます。

離散推定器への最初の引数は常に[`InformationMeasure`](@ref)です（デフォルトは[`Shannon`](@ref)です）。

## 説明

離散[`InformationMeasure`](@ref)は、確率質量関数の関数です。このような測定値をデータから推定するには、まず（エンコードされた/離散化された）入力データから[`ProbabilitiesEstimator`](@ref)を使用して確率質量関数を推定し、その後、推定された確率に推定器を適用する必要があります。たとえば、[`Shannon`](@ref)エントロピーは通常、確率を計算するために[`RelativeAmount`](@ref)推定器を使用し、その後[`PlugIn`](@ref)推定器に渡されます。他にも多くの推定器が存在し、[`Shannon`](@ref)エントロピーだけでなく、他の情報測定値にも対応しています。

私たちは、[`PlugIn`](@ref)や[`Jackknife`](@ref)のような一般的な推定器と、Miller-Madowバイアス補正を使用して[`Shannon`](@ref)エントロピーを計算する専用の推定器である[`MillerMadow`](@ref)の両方のライブラリを提供しています。以下のリストは、完全な概要を示しています。

## 実装

以下の推定器は一般的であり、任意の[`InformationMeasure`](@ref)を計算できます。

  * [`PlugIn`](@ref)。任意の情報測定のデフォルトの一般的プラグイン推定器です。計算された確率質量関数を使用して、定義に記載された通りに測定値を正確に計算します。
  * [`Jackknife`](@ref)。プラグイン推定器とジャックナイフ原理の組み合わせを使用して情報測定を推定します。

### [`Shannon`](@ref)エントロピー推定器

以下の推定器は専用の[`Shannon`](@ref)エントロピー推定器であり、ナイーブな[`PlugIn`](@ref)推定器に対して改善を提供します。

  * [`MillerMadow`](@ref)。
  * [`HorvitzThompson`](@ref)。
  * [`Schuermann`](@ref)。
  * [`GeneralizedSchuermann`](@ref)。
  * [`ChaoShen`](@ref)。

!!! info
    実装された任意の[`DiscreteInfoEstimator`](@ref)は、[`information`](@ref)への入力として*任意の*[`ProbabilitiesEstimator`](@ref)と組み合わせて使用できます。これは、すべての推定器が実際には多くの異なるバリアントで提供されることを意味します - 各[`ProbabilitiesEstimator`](@ref)ごとに1つずつです。たとえば、[`Shannon`](@ref)エントロピーの[`MillerMadow`](@ref)推定器は通常、[`RelativeAmount`](@ref)確率で計算されます。しかし、ここでは、たとえば[`BayesianRegularization`](@ref)や[`Shrinkage`](@ref)確率推定器を代わりに使用できます。つまり、`information(MillerMadow(), RelativeAmount(outcome_space), x)`と`information(MillerMadow(), BayesianRegularization(outcomes_space), x)`は異なる推定器です。これはすべての[`DiscreteInfoEstimator`](@ref)に当てはまります。これらの推定器の多くは、これまで文献で探求されていないため、自由に探求してください。また、新しい推定器の組み合わせを探求する際には、このソフトウェアを引用してください！

