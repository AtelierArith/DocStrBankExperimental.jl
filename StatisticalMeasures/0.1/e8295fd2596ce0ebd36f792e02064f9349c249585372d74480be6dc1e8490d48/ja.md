```
MisclassificationRate()
```

呼び出し可能な指標を返し、誤分類率を計算します。エイリアス: `misclassification_rate`, `mcr`.

```
MisclassificationRate()(ŷ, y)
MisclassificationRate()(ŷ, y, weights)
MisclassificationRate()(ŷ, y, class_weights::AbstractDict)
MisclassificationRate()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `MisclassificationRate()` を評価し、真の観測値 `y` を考慮します。つまり、予測 `ŷᵢ` が対応する真の値 `yᵢ` と異なる割合を返します。より一般的には、誤って識別された観測値に対して指定された重みの平均を計算します。混同行列に対しても呼び出すことができます。 [`ConfusionMatrix`](@ref) を参照してください。

この指標はクラスの順序変更に対して不変です。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(MisclassificationRate(), ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (多クラス分類) を満たすことが期待されます。

[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

利用可能な指標の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = misclassification rate
```
