```
FeatureSelector
```

特徴選択器を構築するためのモデルタイプで、[unknown.jl](unknown)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
FeatureSelector = @load FeatureSelector pkg=unknown
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = FeatureSelector()`を使用します。ハイパーパラメータのデフォルトを上書きするには、`FeatureSelector(features=...)`のようにキーワード引数を提供します。

このモデルを使用して、通常はモデルの`Pipeline`の一部として、テーブルの特徴（列）を選択します。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで

  * `X`: 入力特徴の任意のテーブルで、「テーブル」はTables.jlの意味で使用されます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `features`: 次のいずれかで、動作は以下の通りです。

      * `[]`（空、デフォルト）：トレーニング中に遭遇しなかったすべての特徴（列）をフィルタリングします
      * 特徴名（シンボル）の非空ベクター：指定された特徴のみを保持する（`ignore=false`）か、指定されていない特徴のみを保持する（`ignore=true`）
      * 関数または他の呼び出し可能なもの：呼び出し可能なものがその名前に対して`true`を返す場合、特徴を保持します。たとえば、`FeatureSelector(features = name -> name in [:x1, :x3], ignore = true)`を指定することは、`FeatureSelector(features = [:x1, :x3], ignore = true)`と同じ効果を持ち、すなわち`:x1`と`:x3`を除くすべての特徴を選択します。
  * `ignore`: 上記のように指定された`features`を無視するか保持するか

# 操作

  * `transform(mach, Xnew)`: トレーニング中に見た特徴を考慮しながら、モデルによって指定されたようにテーブル`Xnew`から特徴を選択します

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次の通りです。

  * `features_to_keep`: 選択される特徴

# 例

```
using MLJ

X = (ordinal1 = [1, 2, 3],
     ordinal2 = coerce(["x", "y", "x"], OrderedFactor),
     ordinal3 = [10.0, 20.0, 30.0],
     ordinal4 = [-20.0, -30.0, -40.0],
     nominal = coerce(["Your father", "he", "is"], Multiclass));

selector = FeatureSelector(features=[:ordinal3, ], ignore=true);

julia> transform(fit!(machine(selector, X)), X)
(ordinal1 = [1, 2, 3],
 ordinal2 = CategoricalValue{Symbol,UInt32}["x", "y", "x"],
 ordinal4 = [-20.0, -30.0, -40.0],
 nominal = CategoricalValue{String,UInt32}["Your father", "he", "is"],)

```
