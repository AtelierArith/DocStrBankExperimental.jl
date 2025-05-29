```
AreaUnderCurve()
```

受信者操作特性の下の面積を計算するための呼び出し可能な測定値を返します。エイリアス: `auc`, `area_under_curve`.

```
AreaUnderCurve()(ŷ, y)
```

真の観測値 `y` に対して予測 `ŷ` で `AreaUnderCurve()` を評価します。定義については、[*受信者操作特性*](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) のWikipedia記事を参照してください。`ŷ` は、特に `y` のユニークな要素のバイナリセットに対する分布のベクトルであることが期待されます。具体的には、`ŷ` はCategoricalDistributions.jlパッケージの `<:UnivariateFinite` の型を持つ必要があります。

実装はマン・ホイットニーU統計量に基づいています。詳細については、[*ホイットニーU検定*](https://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test#Area_under_curve_(AUC)_statistic_for_ROC_curves) のWikipediaページを参照してください。

コア実装: [`Functions.auc`](@ref).

このメトリックはクラスの順序変更に対して不変です。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``ScientificTypesBase.Binary` を満たすことが期待されます。

[`roc_curve`](@ref) も参照してください。

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = ScientificTypesBase.Binary
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = 受信者操作特性の下の面積
```
