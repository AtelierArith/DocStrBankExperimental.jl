```
RSquared()
```

R²係数を計算するための呼び出し可能な測定値を返します。エイリアス: `rsq`, `rsquared`.

```
RSquared()(ŷ, y)
```

真の観測値 `y` に対して予測 `ŷ` で `RSquared()` を評価します。具体的には、次の値を返します。

$$
1 - \frac{∑ᵢ (ŷ_i- y_i)^2}{∑ᵢ ȳ - y_i)^2},
$$

ここで $ȳ$ は $y_i$ の平均を示します。R-squared または決定係数としても知られる `R²` 係数は、線形回帰分析の解釈に適しています (Chicco et al., [2021](https://doi.org/10.7717/peerj-cs.623))。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`` を満たすことが期待されます。

利用可能な測定値の完全な辞書は、コンストラクタに基づいてキー付けされており、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = R² coefficient
```
