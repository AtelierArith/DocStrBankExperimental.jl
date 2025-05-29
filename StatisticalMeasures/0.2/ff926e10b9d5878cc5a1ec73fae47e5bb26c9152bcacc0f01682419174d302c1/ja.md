```
BrierScore()
```

呼び出し可能なBrierスコアを計算するための測定値を返します。エイリアス: `brier_score`, `quadratic_score`.

```
BrierScore()(ŷ, y)
BrierScore()(ŷ, y, weights)
BrierScore()(ŷ, y, class_weights::AbstractDict)
BrierScore()(ŷ, y, weights, class_weights::AbstractDict)
```

真の観測値 `y` に対して予測 `ŷ` で `BrierScore()` を評価します。スコアは観測スコアの平均です。一般的に、観測スコアは平均化する前に指定された重みで前乗算されます。確率的予測 `ŷ` が取るべき形式については、以下を参照してください。

Gneiting と Raftery [(2007)](https://doi.org/10.1198/016214506000001437) における慣例、「厳密適正スコアリングルール、予測、および推定」

*有限ケース.* `p(η)` が *単一* 観測 `η` の予測確率であり、`C` がすべての可能なクラスである場合、その例に対応するスコアは次のように与えられます。

$$
2p(η) - \left(\sum_{c ∈ C} p(c)^2\right) - 1
$$

*警告.* `BrierScore()` は「スコア」の意味であり、大きいほど良い（最適は `0` で、他のすべての値は負）。Brier の1950年の元の論文や多くの他の場所では、名前にもかかわらず、逆の符号を持っています。さらに、現在の実装はバイナリケースを特別扱いしないため、スコアは他の使用法と比べてバイナリケースで2倍の差が生じる可能性があります。

*無限ケース.* 上記の合計を積分に置き換えることは、`Continuous` または `Count` ターゲット `y` の場合にここで採用された式には *ならない*。むしろ、上記の論文で採用された慣例が採用され、次のスコアが返されます。

$$
2p(η) - ∫ p(t)^2 dt
$$

`Continuous` ケース（`p` は確率密度関数）または

$$
2p(η) - ∑_t p(t)^2
$$

`Count` ケース（`p` は確率質量関数）で。

予測 `ŷ` は、`Finite` ターゲット `y` の場合は CategoricalDistritutions.jl からの `UnivariateFinite` 分布のベクトルである必要があり、そうでない場合は `Normal` や `Poisson` などのサポートされている `Distributions.UnivariateDistribution` である必要があります。

符号のみが異なる [`BrierLoss`](@ref) も参照してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは、`y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(BrierScore(), ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Missing,T}` を満たすことが期待され、ここで `T` は `Continuous` または `Count` です（それぞれ `ŷ` の連続または離散の Distribution.jl オブジェクト用）または `OrderedFactor` または `Multiclass`（`ŷ` の `UnivariateFinite` 分布用）。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = brier score
```
