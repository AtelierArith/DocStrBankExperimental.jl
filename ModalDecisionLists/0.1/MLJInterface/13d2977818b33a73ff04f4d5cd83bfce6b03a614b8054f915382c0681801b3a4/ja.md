```
    ExtendedSequentialCovering
```

モデルトタイプは、ModalDecisionLists.jlに基づいて逐次カバリング分類器を構築し、MLJモデルインターフェースを実装します。

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = ExtendedSequentialCovering()`を実行します。ハイパーパラメータのデフォルトを上書きするには、`ExtendedSequentialCovering(searchmethod=...)`のようにキーワード引数を提供します。

## トレーニングデータ

MLJまたはMLJBaseでは、インスタンスモデルをデータにバインドするには

`mach = machine(model, X, y)`

を使用します。ここで、

  * X: 入力特徴のアンテーブル（例：DataFrame）；TODO ここから続ける....
  * y: ターゲットで、要素のscitypeが <:MultiClass である任意のAbstractVector；scitype(y)でscitypeを確認します。

`fit!(mach, rows=...)`でマシンをトレーニングします。

## ハイパーパラメータ

  * `searchmethod::SearchMethod=BeamSearch()`: 単一ルールを見つけるための検索方法（[`SearchMethod`](@ref)を参照）。
  * `max_rulebase_length::Union{Nothing,Integer}=nothing`はルールベースの最大長です。
  * `min_rule_coverage::Integer=1`: 各ルールによってカバーされるインスタンスの最小数を制約します。
  * `suppress_parity_warning::Bool=false`: `true`の場合、パリティ警告を抑制します。

## フィッティングパラメータ

fitted_params(mach)のフィールドは次のとおりです：

  * `fitresult`: `DecisionList`オブジェクト。

## 操作

  * `predict(mach, Xnew)`: Xnewの各行に対する予測のベクトルを返します。

[`SearchMethod`](@ref)も参照してください。
