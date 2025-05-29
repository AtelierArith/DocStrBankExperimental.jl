```
FScore(; beta=1.0, levels=nothing, rev=nothing, checks=true)
```

$$
F_β
$$

スコアを計算するための呼び出し可能な測定値を返します。エイリアス: `f1score`。

```
m(ŷ, y)
```

予測 `ŷ` に対して、真の観測値 `y` が与えられたときに、`FScore` コンストラクタによって返された測定値 `m`（例: `m = FScore()`）を評価します。これは、$F$-測定またはバランスの取れた $F$-スコアの一変数一般化、$F_β$ です。`beta=β` を範囲 $[0,∞]$ で選択し、`beta > 1` を使用して精度（[`PositivePredictiveValue`](@ref)）よりも再現率（[`TruePositiveRate`](@ref)）を強調します。`beta = 1` の場合、スコアは精度と再現率の調和平均です。詳細については、[*F1 スコア* Wikipedia ページ](https://en.wikipedia.org/wiki/F-score) を参照してください。

`y` のエレメントタイプに基づいてクラス（レベル）を順序付ける場合、*第二* レベルは「陽性」クラスです。役割を逆転させるには、`rev=true` を指定します。

メソッドは、`levels` が推測される `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

`FScore` 測定値は、混同行列でも呼び出すことができます。 [`ConfusionMatrix`](@ref) を参照してください。

# キーワードオプション

  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、レベルは `ŷ` と `y` から推測され、デフォルトでは `y` のエレメントタイプに従って順序付けられます。
  * `rev=false`: バイナリデータの場合、推測または指定された `levels` を逆転させるかどうか; `nothing` 値は `false` と同じです。
  * `checks=true`: true の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます; スピードのために `false` に設定します。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は、`ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}`（「陽性」クラスの定義が重要なバイナリ分類）を満たすことが期待されます。

[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.fscore`](@ref) 

利用可能な測定値の完全な辞書をコンストラクタに基づいて取得するには、[`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.OrderedFactor{2}}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = ``F_β`` score
```
