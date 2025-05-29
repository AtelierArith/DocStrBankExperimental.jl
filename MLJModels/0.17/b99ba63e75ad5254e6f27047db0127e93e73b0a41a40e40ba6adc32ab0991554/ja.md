```
標準化器
```

[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいて標準化器を構築するためのモデルタイプであり、MLJモデルインターフェースを実装しています。

MLJから、このタイプは次のようにインポートできます。

```
Standardizer = @load Standardizer pkg=MLJModels
```

`model = Standardizer()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`Standardizer(features=...)`のようにキーワード引数を提供します。

このモデルを使用して、`Continuous`ベクトルまたはテーブルの関連する列を標準化（ホワイトニング）します。この変換器が新しいデータに適用する再スケーリングは、トレーニングフェーズ中に学習されたものであり、一般的に新しいデータを実際に標準化するものとは異なります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにインスタンス`model`をデータにバインドします。

```
mach = machine(model, X)
```

ここで

  * `X`: Tables.jl互換のテーブルまたは`Continuous`要素のscitypeを持つ任意の抽象ベクトル（任意の抽象浮動小数点ベクトル）。`Continuous` scitypeを持つテーブルの特徴のみが標準化されます。列のscitypeは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `features`: 以下のいずれかで、動作は以下の通りです。

      * `[]`（空、デフォルト）：`Continuous`要素のscitypeを持つすべての特徴（列）を標準化します。
      * 特徴名（シンボル）の非空ベクトル：ベクトル内の`Continuous`特徴のみを標準化します（`ignore=false`の場合）またはベクトルに名前が付けられていない`Continuous`特徴を標準化します（`ignore=true`の場合）。
      * 関数または他の呼び出し可能なもの：呼び出し可能なものがその名前に対して`true`を返す場合、特徴を標準化します。たとえば、`Standardizer(features = name -> name in [:x1, :x3], ignore = true, count=true)`は、`Standardizer(features = [:x1, :x3], ignore = true, count=true)`と同じ効果を持ち、すべての`Continuous`および`Count`特徴を標準化しますが、`:x1`と`:x3`は除外されます。

    この動作は、`ordered_factor`または`count`フラグが`true`に設定されている場合にさらに修正されます。以下を参照してください。
  * `ignore=false`: 上記のように指定された`features`を無視するか標準化するか
  * `ordered_factor=false`: `true`の場合、`Continuous`特徴が標準化される場所で任意の`OrderedFactor`特徴を標準化します。上記のように説明されています。
  * `count=false`: `true`の場合、`Continuous`特徴が標準化される場所で任意の`Count`特徴を標準化します。上記のように説明されています。

# 操作

  * `transform(mach, Xnew)`: `mach`のフィッティング中に学習された再スケーリングに従って、関連する特徴が標準化された`Xnew`を返します。
  * `inverse_transform(mach, Z)`: `Z`に逆変換を適用し、`inverse_transform(mach, transform(mach, Xnew))`が`Xnew`とほぼ同じになるようにします。`ordered_factor`または`count`フラグが`true`に設定されている場合は利用できません。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `features_fit` - 標準化される特徴の名前
  * `means` - 対応する未変換の平均値
  * `stds` - 対応する未変換の標準偏差

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `features_fit`: 標準化される特徴の名前

# 例

```
using MLJ

X = (ordinal1 = [1, 2, 3],
     ordinal2 = coerce([:x, :y, :x], OrderedFactor),
     ordinal3 = [10.0, 20.0, 30.0],
     ordinal4 = [-20.0, -30.0, -40.0],
     nominal = coerce(["Your father", "he", "is"], Multiclass));

julia> schema(X)
┌──────────┬──────────────────┐
│ names    │ scitypes         │
├──────────┼──────────────────┤
│ ordinal1 │ Count            │
│ ordinal2 │ OrderedFactor{2} │
│ ordinal3 │ Continuous       │
│ ordinal4 │ Continuous       │
│ nominal  │ Multiclass{3}    │
└──────────┴──────────────────┘

stand1 = Standardizer();

julia> transform(fit!(machine(stand1, X)), X)
(ordinal1 = [1, 2, 3],
 ordinal2 = CategoricalValue{Symbol,UInt32}[:x, :y, :x],
 ordinal3 = [-1.0, 0.0, 1.0],
 ordinal4 = [1.0, 0.0, -1.0],
 nominal = CategoricalValue{String,UInt32}["Your father", "he", "is"],)

stand2 = Standardizer(features=[:ordinal3, ], ignore=true, count=true);

julia> transform(fit!(machine(stand2, X)), X)
(ordinal1 = [-1.0, 0.0, 1.0],
 ordinal2 = CategoricalValue{Symbol,UInt32}[:x, :y, :x],
 ordinal3 = [10.0, 20.0, 30.0],
 ordinal4 = [1.0, 0.0, -1.0],
 nominal = CategoricalValue{String,UInt32}["Your father", "he", "is"],)
```

[`OneHotEncoder`](@ref)や[`ContinuousEncoder`](@ref)も参照してください。
