```
MulticlassFalseNegativeRate(; average=macro_avg, levels=nothing, more_options...)
```

マルチクラスの偽陰性率を計算するための呼び出し可能な測定値を返します。エイリアス: `multiclass_false_negative_rate`, `multiclass_falsenegative_rate`, `multiclass_fnr`, `multiclass_miss_rate`.

```
m(ŷ, y)
m(ŷ, y, class_weights::AbstractDict)
```

`MulticlassFalseNegativeRate` コンストラクタによって返された測定値 `m`（例: `m = MulticlassFalseNegativeRate()`）を、真の観測値 `y` に対して予測 `ŷ` で評価します。

これは、バイナリの [`FalseNegativeRate`](@ref) の平均化された一対多のバージョンです。また、ターゲットクラス（またはベクトル）をキーにした辞書を返すこともできます。以下の `average` オプションを参照してください。

メソッドは、`levels` が推測された `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

混同行列に対しても `m` を呼び出すことができます。混同行列は [`ConfusionMatrix`](@ref) を使用して構築します。

`class_weights` のキーは、`y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は、`ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}`（"positive" クラスの定義が重要なバイナリ分類）を満たすことが期待されます。

# キーワードオプション

  * `average=MacroAvg()`: `NoAvg()`, `MacroAvg()`, `MicroAvg()` のいずれか（StatisticalMeasuresBase.jl によって所有され、エクスポートされる名前）。J. Opitz と S. Burst [(2019)](https://arxiv.org/abs/1911.03347) を参照してください。「Macro F1 と Macro F1」、*arXiv*。
  * `return_type=LittleDict`: `average=NoAvg()` の場合に返される測定値の型; `LittleDict` の場合、ターゲットのレベルにキー付けされます; または `Vector` であることもできます。
  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、`ŷ` と `y` からレベルが推測され、デフォルトでは `y` の要素型に従って順序付けされます。
  * `rev=false`: バイナリデータの場合、`levels`（推測または指定されたもの）を反転するかどうか; `nothing` の値は `false` と同じです。
  * `perm=nothing`: 一般的な場合、`levels`（推測または指定されたもの）の再順序を表す置換; 例: 三つのクラスを持つデータの場合 `perm = [1,3,2]`。
  * `checks=true`: true の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます; スピードのために `false` に設定します。

メソッドは、`levels` が推測された `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

また、[`FalseNegativeRate`](@ref)、[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.multiclass_false_negative_rate`](@ref)

利用可能な測定値の完全な辞書を、コンストラクタにキー付けして取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = multi-class false negative rate
```
