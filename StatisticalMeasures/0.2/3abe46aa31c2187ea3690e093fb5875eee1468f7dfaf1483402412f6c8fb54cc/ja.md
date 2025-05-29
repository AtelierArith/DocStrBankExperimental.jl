```
MulticlassTruePositive(; levels=nothing, more_options...)
```

マルチクラスの真陽性カウントを計算するための呼び出し可能な測定値を返します。エイリアス: `multiclass_true_positive`, `multiclass_truepositive`.

```
m(ŷ, y)
```

予測 `ŷ` に対して、真の観測値 `y` が与えられたときに、`MulticlassTruePositive` コンストラクタによって返された測定値 `m` を評価します（例: `m = MulticlassTruePositive()`）。 

これは、バイナリ測定 [`TruePositive`](@ref) の一対多のバージョンであり、単一の数値ではなく、ターゲットクラス（レベル）にキー付けされた辞書、またはベクトル（以下のオプションを参照）を返します。バイナリデータでも同様です。

メソッドは、`levels` が推測された `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

`m` は混同行列に対しても呼び出すことができます。混同行列は [`ConfusionMatrix`](@ref) を使用して構築します。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は、`ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}`（「陽性」クラスの定義が重要なバイナリ分類）を満たすことが期待されます。

# キーワードオプション

  * `return_type=LittleDict`: `average=NoAvg()` の場合に返される測定値のタイプ; `LittleDict` の場合、ターゲットのレベルにキー付けされます; `Vector` でも可能です。
  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、`ŷ` と `y` からレベルが推測され、デフォルトでは `y` の要素タイプに従って順序付けされます。
  * `rev=false`: バイナリデータの場合、`levels`（推測または指定されたもの）を反転するかどうか; `nothing` の値は `false` と同じです。
  * `perm=nothing`: 一般的な場合、`levels`（推測または指定されたもの）の再順序を表す置換; 例: 三つのクラスを持つデータの場合 `perm = [1,3,2]`。
  * `checks=true`: true の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます; スピードのために `false` に設定します。

メソッドは、`levels` が推測された `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

[`TruePositive`](@ref)、[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.multiclass_true_positive`](@ref)

利用可能な測定値の完全な辞書を、コンストラクタにキー付けして取得するには、[`measures()`](@ref) を実行してください。

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
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = マルチクラス真陽性カウント
```
