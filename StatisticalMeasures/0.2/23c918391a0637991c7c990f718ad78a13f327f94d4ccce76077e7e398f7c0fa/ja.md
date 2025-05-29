```
FalseNegative(; levels=nothing, rev=nothing, checks=true)
```

呼び出し可能な測定値を返し、偽陰性のカウントを計算します。エイリアス: `false_negative`, `falsenegative`.

```
m(ŷ, y)
```

`FalseNegative` コンストラクタによって返された測定値 `m`（例: `m = FalseNegative()`）を、真の観測値 `y` に対して予測値 `ŷ` で評価します。クラス（レベル）を `y` の要素型に基づいて順序付ける場合、*2番目*のレベルが「正」のクラスとなります。役割を逆にするには、`rev=true` を指定します。

メソッドは、`levels` が推測される `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

`m` は混同行列に対しても呼び出すことができます。 [`ConfusionMatrix`](@ref) を参照してください。

# キーワードオプション

  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、`ŷ` と `y` からレベルが推測され、デフォルトでは `y` の要素型に従って順序付けられます。
  * `rev=false`: バイナリデータの場合、推測または指定された `levels` を逆にするかどうか; `nothing` の値は `false` と同じです。
  * `checks=true`: `true` の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます; スピードのために `false` に設定します。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}`（「正」のクラスの定義が重要なバイナリ分類）を満たすことが期待されます。

[`MulticlassFalseNegative`](@ref)、[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref)、および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.false_negative`](@ref)

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.OrderedFactor{2}}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = 偽陰性カウント
```
