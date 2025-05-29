```
BalancedAccuracy(; adjusted=false)
```

バランスの取れた精度を計算するための呼び出し可能な測定値を返します。エイリアス: `balanced_accuracy`, `bacc`, `bac`, `probability_of_correct_classification`.

```
m(ŷ, y)
m(ŷ, y, weights)
```

予測 `ŷ` に対して、真の観測値 `y` を考慮して `BalancedAccuracy` コンストラクタによって返された測定値 `m` を評価します（例: `m = BalancedAccuracy()`）。これは、クラスの不均衡を補正する [`Accuracy`](@ref) のバリエーションです。詳細は [https://en.wikipedia.org/wiki/Precision*and*recall#Imbalanced_data](https://en.wikipedia.org/wiki/Precision_and_recall#Imbalanced_data) を参照してください。

`adjusted=true` に設定すると、[L. Mosley (2013)](https://lib.dr.iastate.edu/etd/13537/) で規定された方法でスコアが再スケールされます: 多クラスの不均衡問題に対するバランスの取れたアプローチ。博士論文、アイオワ州立大学。バイナリの場合、調整されたバランスの取れた精度は *Youden’s J statistic* または *informedness* としても知られています。

混同行列に対しても呼び出すことができます。詳細は [`ConfusionMatrix`](@ref) を参照してください。

この指標はクラスの順序変更に対して不変です。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (多クラス分類) を満たすことが期待されます。

利用可能な測定値の完全な辞書は、コンストラクタに基づいてキー付けされており、[`measures()`](@ref) を実行することで確認できます。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = balanced accuracy
```
