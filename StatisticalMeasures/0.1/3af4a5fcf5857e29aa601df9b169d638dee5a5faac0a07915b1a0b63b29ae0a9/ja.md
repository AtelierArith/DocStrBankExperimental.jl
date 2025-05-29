```
SphericalScore()
```

球面スコアを計算するための呼び出し可能な測定値を返します。エイリアス: `spherical_score`。

```
SphericalScore()(ŷ, y)
SphericalScore()(ŷ, y, weights)
SphericalScore()(ŷ, y, class_weights::AbstractDict)
SphericalScore()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `SphericalScore()` を評価し、真の観測値 `y` を与えます。スコアは観測スコアの平均です。一般的に、観測スコアは平均化の前に指定された重みで前乗算されます。確率的予測 `ŷ` が取るべき形式については、以下を参照してください。

Gneiting と Raftery [(2007)](https://doi.org/10.1198/016214506000001437) の慣例に従い、「厳密に適切なスコアリングルール、予測、および推定」: `y` が有限のクラス `C` を取る場合、`p(y)` は単一の観測 `y` に対する予測確率であり、その例に対する対応するスコアは次のように与えられます。

$$
p(y)^α / \left(\sum_{η ∈ C} p(η)^α\right)^{1-α} - 1
$$

ここで `α` は測定パラメータ `alpha` です。

予測 `ŷ` が `Distributions.Normal` のような連続確率分布である場合、上記の合計を積分に置き換え、`p` を確率密度関数として解釈します。整数に対する離散分布、例えば `Distributions.Poisson` の場合は、`C` の代わりにすべての整数を合計します。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値に対するすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値に対して別々の測定値を取得するには、構文 `measurements(SphericalScore(), ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Missing,T}` を満たすことが期待され、ここで `T` は `Continuous` または `Count`（それぞれ `ŷ` の連続または離散の Distribution.jl オブジェクト用）または `OrderedFactor` または `Multiclass`（`ŷ` の `UnivariateFinite` 分布用）です。

利用可能な測定値の完全な辞書をコンストラクタに基づいて取得するには、[`measures()`](@ref) を実行します。

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
human_name = spherical score
```
