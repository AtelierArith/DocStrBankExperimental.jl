```
ConfusionMatrix(; levels=nothing, rev=false, perm=nothing, checks=true)
```

呼び出し可能な混同行列を計算するための測定値を返します。エイリアス: `confmat`, `confusion_matrix`.

```
m(ŷ, y)
```

予測 `ŷ` に対して、真の観測値 `y` が与えられたときに、`ConfusionMatrix` コンストラクタによって返された測定値 `m` を評価します（例: `m = ConfusionMatrix()`）。詳細は [*混同行列* のウィキペディア記事](https://en.wikipedia.org/wiki/Confusion_matrix) を参照してください。

混同行列の要素には常にレベルによってアクセスできます - 以下の例を参照してください。混同行列を順序付きとしてフラグを立て、インデックスアクセス可能にするには、次のいずれかを行います：

  * 順序付きの `CategoricalArray` 入力 `ŷ` と `y` を提供する
  * `levels` または `rev`, `perm` のいずれかを明示的に指定する

2つの混同行列に対する `==` は、両方が順序付きの場合に厳密になります。

一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}`（多クラス分類）を満たすことが期待されます。

# キーワードオプション

  * `levels::Union{Vector,Nothing}=nothing`: `nothing` の場合、レベルは `ŷ` と `y` から推測され、デフォルトでは `y` の要素タイプに従って順序付けられます。
  * `rev=false`: バイナリデータの場合、`levels`（推測または指定された）を反転するかどうか；`nothing` の値は `false` と同じです。
  * `perm=nothing`: 一般的な場合、`levels` の再順序を表す置換（推測または指定された）；例: 3クラスのデータに対して `perm = [1,3,2]`。
  * `checks=true`: true の場合、指定された `levels` がすべての観測されたレベルを含むかどうかがチェックされます；速度のために `false` に設定します。

メソッドは、`levels` が推測された `CategoricalArray` 入力に最適化されています。その場合、`levels` は完全な内部クラスプールとなり、観測されたレベルだけではありません。

返されるオブジェクトのタイプとそのインターフェースの詳細については、[`ConfusionMatrices.ConfusionMatrix`](@ref) を参照してください。

# 例

```julia

using StatisticalMeasures

y = ["a", "b", "a", "a", "b", "a", "a", "b", "b", "a"]
ŷ = ["b", "a", "a", "b", "a", "b", "b", "b", "a", "a"]

julia> cm = ConfusionMatrix()(ŷ, y)  # または `confmat((ŷ, y)`.

              ┌───────────────────────────┐
              │       真の値             │
┌─────────────┼─────────────┬─────────────┤
│  予測値     │      a      │      b      │
├─────────────┼─────────────┼─────────────┤
│      a      │      2      │      3      │
├─────────────┼─────────────┼─────────────┤
│      b      │      4      │      1      │
└─────────────┴─────────────┴─────────────┘

julia> cm("a", "b")
3
```

コアアルゴリズム:  [`ConfusionMatrices.confmat`](@ref).

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいて [`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Unoriented()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = 混同行列
```
