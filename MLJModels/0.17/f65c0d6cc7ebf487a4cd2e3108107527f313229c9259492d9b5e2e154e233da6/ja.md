```
UnivariateDiscretizer
```

単一変数の離散化器を構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
UnivariateDiscretizer = @load UnivariateDiscretizer pkg=MLJModels
```

`model = UnivariateDiscretizer()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`UnivariateDiscretizer(n_classes=...)`のようにキーワード引数を提供します。

離散化は、`Continuous`ベクトルを`OrderedFactor`ベクトルに変換します。特に、出力は`CategoricalVector`（その参照タイプは最適化されています）です。

変換は、トランスフォーマーがフィットするベクトルが、変換された形で値のほぼ均一な分布を持つように選択されます。具体的には、`n_classes`が離散化のレベルである場合、`2*n_classes - 1`の順序付き分位点が計算され、奇数の分位点が変換（離散化）に使用され、偶数の分位点が逆変換に使用されます。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, x)
```

ここで

  * `x`: `Continuous`要素のscitypeを持つ任意の抽象ベクトル; `scitype(x)`でscitypeを確認します。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `n_classes`: 出力の離散クラスの数

# 操作

  * `transform(mach, xnew)`: `mach`をフィットさせる際に学習した離散化に従って`xnew`を離散化します
  * `inverse_transform(mach, z)`: `z`から再構築を試み、`z`を与えるベクトルを変換します

# フィッティングされたパラメータ

`fitted_params(mach).fitesult`のフィールドには以下が含まれます：

  * `odd_quantiles`: 変換に使用される分位点（長さは`n_classes - 1`）
  * `even_quantiles`: 逆変換に使用される分位点（長さは`n_classes`）

# 例

```
using MLJ
using Random
Random.seed!(123)

discretizer = UnivariateDiscretizer(n_classes=100)
mach = machine(discretizer, randn(1000))
fit!(mach)

julia> x = rand(5)
5-element Vector{Float64}:
 0.8585244609846809
 0.37541692370451396
 0.6767070590395461
 0.9208844241267105
 0.7064611415680901

julia> z = transform(mach, x)
5-element CategoricalArrays.CategoricalArray{UInt8,1,UInt8}:
 0x52
 0x42
 0x4d
 0x54
 0x4e

x_approx = inverse_transform(mach, z)
julia> x - x_approx
5-element Vector{Float64}:
 0.008224506144777322
 0.012731354778359405
 0.0056265330571125816
 0.005738175684445124
 0.006835652575801987
```
