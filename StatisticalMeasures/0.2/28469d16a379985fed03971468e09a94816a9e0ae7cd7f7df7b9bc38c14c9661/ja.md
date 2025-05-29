```
LogScore(; tol=eps())
```

ログスコアを計算するための呼び出し可能な測定値を返します。エイリアス: `log_score`。

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して、真の観測値 `y` を考慮して `LogScore` コンストラクタによって返される測定値 `m` を評価します（例: `m = LogScore()`）。スコアは観測スコアの平均です。一般的に、観測スコアは平均化の前に指定された重みで前乗算されます。確率的予測 `ŷ` が取るべき形式については以下を参照してください。生の確率は `0` と `1` からクランプされます。具体的には、`p` が与えられた真の観測値 `η` で評価された確率質量/密度関数である場合、その例のスコアは次のように定義されます。

```
log(clamp(p(η), tol, 1 - tol).
```

例えば、バイナリターゲットで「はい」/「いいえ」ラベルがある場合、確率的予測が「はい」に対して 0.8 のスコアを持つとき、対応する真の観測値が「いいえ」であれば、その例のスコアへの寄与は `log(0.2)` です。

予測 `ŷ` は、`Finite` ターゲット `y`（`CategoricalVector`）の場合、CategoricalDistritutions.jl からの `UnivariateFinite` 分布のベクトルである必要があり、そうでない場合は `Normal` や `Poisson` などのサポートされている `Distributions.UnivariateDistribution` である必要があります。

サインのみが異なる [`LogLoss`](@ref) も参照してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(m, ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Missing,T}` を満たすことが期待され、ここで `T` は `Continuous` または `Count`（それぞれ `ŷ` の連続または離散の Distribution.jl オブジェクトの場合）または `OrderedFactor` または `Multiclass`（`ŷ` の `UnivariateFinite` 分布の場合）です。

利用可能な測定値の完全な辞書を取得するには、[`measures()`](@ref) を実行してください。

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
human_name = log score
```
