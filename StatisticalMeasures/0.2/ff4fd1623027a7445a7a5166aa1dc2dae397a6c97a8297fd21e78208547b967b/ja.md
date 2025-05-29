```
LPLoss(; p=2)
```

呼び出し可能な測定値を返し、$L^p$損失を計算します。エイリアス: `l1`, `l2`, `mae`, `mav`, `mean_absolute_error`, `mean_absolute_value`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

`LPLoss`コンストラクタによって返される測定値`m`（例: `m = LPLoss()`）を、真の観測値`y`に対して予測値`ŷ`に適用します。具体的には、すべての観測ペア$(ŷ_i, y_i)$に対して$|ŷ_i - y_i|^p$の平均を返します。より一般的には、それらの値の加重バージョンの平均を返します。加重*合計*には[`LPSumLoss`](@ref)を使用してください。

`Real`要素を生成する`length`を持つ任意のイテレータを`weights`として使用できます。`class_weights`のキーは、`y`の観測値に対して考えられるすべての値を含む必要があり、値は`Real`である必要があります。

測定値は集約されます。各観測値に対して別々の測定値を取得するには、構文`measurements(m, ŷ, y)`を使用します。一般的に、`MLUtils.eachobs(y)`の観測値`obs`は、`ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}``を満たすことが期待されます。

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref)を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = ``L^p`` loss
```
