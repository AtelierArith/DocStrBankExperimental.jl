```
UnivariateFillImputer
```

単一変数フィルインプーターを構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
UnivariateFillImputer = @load UnivariateFillImputer pkg=MLJModels
```

`model = UnivariateFillImputer()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`UnivariateFillImputer(continuous_fill=...)`のようにキーワード引数を提供します。

このモデルを使用して、トレーニングベクトルの非欠損値から学習した固定値でベクトル内の`missing`値を補完します。

表形式のデータの欠損値を補完するには、代わりに[`FillImputer`](@ref)を使用してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, x)
```

ここで

  * `x`: 要素のscitypeが`Union{Missing, T}`である任意の抽象ベクトルで、`T`は`Continuous`、`Multiclass`、`OrderedFactor`または`Count`のサブタイプです。`scitype(x)`を使用してscitypeを確認します。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `continuous_fill`: `Continuous`（抽象浮動小数点）データの場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に`median`を適用することです。
  * `count_fill`: `Count`（整数）データの場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に丸めた`median`を適用することです。
  * `finite_fill`: `Multiclass`または`OrderedFactor`データ（カテゴリカルベクトル）の場合に補完される値を決定する関数または他の呼び出し可能なもの; デフォルトは`missing`値をスキップした後に`mode`を適用することです。

# 操作

  * `transform(mach, xnew)`: `mach`をフィッティングする際に学習したフィル値で補完された`xnew`を返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `filler`: 新しいすべてのデータに補完されるフィル値

# 例

```
using MLJ
imputer = UnivariateFillImputer()

x_continuous = [1.0, 2.0, missing, 3.0]
x_multiclass = coerce(["y", "n", "y", missing, "y"], Multiclass)
x_count = [1, 1, 1, 2, missing, 3, 3]

mach = machine(imputer, x_continuous)
fit!(mach)

julia> fitted_params(mach)
(filler = 2.0,)

julia> transform(mach, [missing, missing, 101.0])
3-element Vector{Float64}:
 2.0
 2.0
 101.0

mach2 = machine(imputer, x_multiclass) |> fit!

julia> transform(mach2, x_multiclass)
5-element CategoricalArray{String,1,UInt32}:
 "y"
 "n"
 "y"
 "y"
 "y"

mach3 = machine(imputer, x_count) |> fit!

julia> transform(mach3, [missing, missing, 5])
3-element Vector{Int64}:
 2
 2
 5
```

表形式のデータを補完するには、[`FillImputer`](@ref)を使用してください。
