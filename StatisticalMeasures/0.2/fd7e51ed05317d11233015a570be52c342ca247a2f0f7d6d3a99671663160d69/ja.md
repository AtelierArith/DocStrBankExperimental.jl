```
MultitargetLPSumLoss(; p=2, atomic_weights=nothing)
```

マルチターゲット $L^p$ 合計損失を計算するための呼び出し可能な測定値を返します。エイリアス: `multitarget_l1_sum`, `multitarget_l2_sum`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

`MultitargetLPSumLoss` コンストラクタによって返された測定値 `m` を、真の観測値 `y` に対して予測値 `ŷ` で評価します。具体的には、[`LPSumLoss`](@ref) のマルチターゲットバージョンを計算します。いくつかの種類の表形式の入力がサポートされています。

配列引数では、最後の次元が観測次元であると理解されます。`atomic_weights` はマルチターゲットの各コンポーネントの重みです。`nothing`（均一重み）と等しくない限り、`atomic_weights` の長さは一般に `y` の列数と一致するか、`y` が行列である場合は `y` の行数と一致します。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(m, ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``AbstractArray{<:Union{Missing,Infinite}}` を満たすことが期待されます。あるいは、`y` と `ŷ` は、要素が適切なスカイタイプを持つ限り、いくつかの種類の表であることができます。

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = AbstractArray{<:Union{Missing, ScientificTypesBase.Infinite}}
can_consume_tables = true
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = multitarget ``L^p`` sum loss
```
