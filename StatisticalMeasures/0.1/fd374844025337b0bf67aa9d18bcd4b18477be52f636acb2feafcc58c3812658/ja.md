```
TrueNegative(; levels=nothing, rev=nothing, checks=true)
```

真の陰性カウントを計算するための呼び出し可能な測定値を返します。エイリアス: `true_negative`, `truenegative`.

```
m(ŷ, y)
```

予測 `ŷ` に対して、真実の観測 `y` を考慮して `TrueNegative` コンストラクタによって返された測定値 `m` を評価します（例: `m = TrueNegative()`）。クラス（レベル）を `y` のエレメントタイプに基づいて順序付ける場合、*第二* レベルが「正」のクラスとなります。役割を逆にするには、`rev=true` を指定します。

メソッドは、`levels` が推測される `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

`m` は混同行列に対しても呼び出すことができます。 [`ConfusionMatrix`](@ref) を参照してください。

# キーワードオプション

  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、`ŷ` と `y` からレベルが推測され、デフォルトでは `y` のエレメントタイプに従って順序付けられます。
  * `rev=false`: バイナリデータの場合、推測または指定された `levels` を逆にするかどうか; `nothing` の値は `false` と同じです。
  * `checks=true`: true の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます; スピードのために `false` に設定します。

一般に、`MLUtils.eachobs(y)` の観測 `obs` は `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}`（「正」のクラスの定義が重要なバイナリ分類）を満たすことが期待されます。

[`MulticlassTrueNegative`](@ref)、[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref)、および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.true_negative`](@ref)

利用可能な測定値の完全な辞書をコンストラクタに基づいて取得するには、[`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.OrderedFactor{2}}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = true negative count
```
