```
Kappa()
```

コーエンのκを計算するための呼び出し可能な測定値を返します。エイリアス: `kappa`。

```
Kappa()(ŷ, y)
Kappa()(ŷ, y, weights)
```

真の観測値 `y` に対して予測 `ŷ` で `Kappa()` を評価します。詳細については、[Cohen's κ](https://en.wikipedia.org/wiki/Cohen%27s_kappa) のWikipedia記事を参照してください。混同行列に対しても呼び出すことができます。[`ConfusionMatrix`](@ref) を参照してください。

この指標はクラスの順序変更に対して不変です。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (多クラス分類) を満たすことが期待されます。

[`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) および [`ConfusionMatrix`](@ref) も参照してください。

コアアルゴリズム: [`Functions.kappa`](@ref)

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = Cohen's κ
```
