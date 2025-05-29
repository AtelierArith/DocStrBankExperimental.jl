```
MatthewsCorrelation()
```

マシューズ相関を計算するための呼び出し可能な測定値を返します。エイリアス: `matthews_correlation`, `mcc`.

```
MatthewsCorrelation()(ŷ, y)
```

真の観測値 `y` に対して予測 `ŷ` で `MatthewsCorrelation()` を評価します。詳細は[ウィキペディアの *マシューズ相関* ページ](https://en.wikipedia.org/wiki/Matthews_correlation_coefficient)を参照してください。混同行列に対しても呼び出すことができます。詳細は[`ConfusionMatrix`](@ref)を参照してください。

このメトリックはクラスの順序変更に対して不変です。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}`（多クラス分類）を満たすことが期待されます。

さらに[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref)および[`ConfusionMatrix`](@ref)も参照してください。

コアアルゴリズム: [`Functions.matthews_correlation`](@ref)

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいて[`measures()`](@ref)を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = マシューズ相関
```
