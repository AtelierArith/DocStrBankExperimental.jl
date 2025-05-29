```
FillImputer
```

[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいてフィルインプーターを構築するためのモデルタイプであり、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
FillImputer = @load FillImputer pkg=MLJModels
```

`model = FillImputer()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`FillImputer(features=...)`のようにキーワード引数を提供します。

このモデルを使用して、表形式データの`missing`値を補完します。固定の「フィラー」値は、テーブルの各列ごとにトレーニングデータから学習されます。

ベクトルの欠損値を補完するには、代わりに[`UnivariateFillImputer`](@ref)を使用してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで

  * `X`: 各列が要素のscitypes `Union{Missing, T}`を持つ入力特徴の任意のテーブル（例：`DataFrame`）で、`T`は`Continuous`、`Multiclass`、`OrderedFactor`または`Count`のサブタイプです。scitypesは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `features`: 補完を試みる特徴（シンボル）の名前のベクトル; デフォルトは空で、これは「すべてを補完する」と解釈されます。
  * `continuous_fill`: `Continuous`（抽象浮動小数点）データの場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に`median`を適用します。
  * `count_fill`: `Count`（整数）データの場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に丸めた`median`を適用します。
  * `finite_fill`: `Multiclass`または`OrderedFactor`データ（カテゴリカルベクトル）の場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に`mode`を適用します。

# 操作

  * `transform(mach, Xnew)`: `mach`をフィッティングする際に学習したフィル値で欠損値を補完した`Xnew`を返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `features_seen_in_fit`: トレーニング中に遭遇した特徴（列）の名前
  * `univariate_transformer`: フィラーを決定するために適用されたユニバリアントモデル（そのフィールドにはフィラー計算を定義する関数が含まれています）
  * `filler_given_feature`: 特徴（列）名をキーとしたフィラー値の辞書

# 例

```
using MLJ
imputer = FillImputer()

X = (a = [1.0, 2.0, missing, 3.0, missing],
     b = coerce(["y", "n", "y", missing, "y"], Multiclass),
     c = [1, 1, 2, missing, 3])

schema(X)
julia> schema(X)
┌───────┬───────────────────────────────┐
│ names │ scitypes                      │
├───────┼───────────────────────────────┤
│ a     │ Union{Missing, Continuous}    │
│ b     │ Union{Missing, Multiclass{2}} │
│ c     │ Union{Missing, Count}         │
└───────┴───────────────────────────────┘

mach = machine(imputer, X)
fit!(mach)

julia> fitted_params(mach).filler_given_feature
(filler = 2.0,)

julia> fitted_params(mach).filler_given_feature
Dict{Symbol, Any} with 3 entries:
  :a => 2.0
  :b => "y"
  :c => 2

julia> transform(mach, X)
(a = [1.0, 2.0, 2.0, 3.0, 2.0],
 b = CategoricalValue{String, UInt32}["y", "n", "y", "y", "y"],
 c = [1, 1, 2, 2, 3],)
```

[`UnivariateFillImputer`](@ref)も参照してください。
