```
MultitargetMisclassificationRate()
```

マルチターゲット誤分類率を計算するための呼び出し可能な測定値を返します。エイリアス: `multitarget_misclassification_rate`, `multitarget_mcr`.

```
MultitargetMisclassificationRate()(ŷ, y)
MultitargetMisclassificationRate()(ŷ, y, weights)
MultitargetMisclassificationRate()(ŷ, y, class_weights::AbstractDict)
MultitargetMisclassificationRate()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `MultitargetMisclassificationRate()` を評価し、真の観測値 `y` を考慮します。具体的には、[`MisclassificationRate`](@ref) のマルチターゲットバージョンを計算します。いくつかの種類の表形式の入力がサポートされています。

配列引数では、最後の次元が観測次元であると理解されます。`atomic_weights` はマルチターゲットの各コンポーネントの重みです。`nothing`（均一な重み）と等しくない限り、`atomic_weights` の長さは一般的に `y` の列数と一致します。`y` が行列の場合は、`y` の行数と一致します。

`weights` には、`Real` 要素を生成する `length` を持つ任意のイテレータを使用できます。`class_weights` のキーは、`y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(MultitargetMisclassificationRate(), ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}`（マルチクラス分類）を満たすことが期待されます。あるいは、`y` と `ŷ` は、要素が適切なスカイタイプを持つ限り、いくつかの種類の表であることができます。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいて [`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = AbstractArray{<:Union{Missing, ScientificTypesBase.Finite}}
can_consume_tables = true
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = multitarget misclassification rate
```
