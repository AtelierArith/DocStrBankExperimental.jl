```
Accuracy()
```

精度を計算するための呼び出し可能な測定値を返します。エイリアス: `accuracy`。

```
Accuracy()(ŷ, y)
Accuracy()(ŷ, y, weights)
Accuracy()(ŷ, y, class_weights::AbstractDict)
Accuracy()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `Accuracy()` を評価し、真の観測値 `y` を与えます。つまり、予測 `ŷᵢ` が対応する真の値 `yᵢ` と一致する割合を計算します。より一般的には、指定された重みをすべての正しく予測された観測値に対して平均します。混同行列に対しても呼び出すことができます。 [`ConfusionMatrix`](@ref) を参照してください。

この指標はクラスの順序変更に対して不変です。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値に対して考えられるすべての値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値に対して別々の測定値を取得するには、構文 `measurements(Accuracy(), ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}`（多クラス分類）を満たすことが期待されます。

[`ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = accuracy
```
