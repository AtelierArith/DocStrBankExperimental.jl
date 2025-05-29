```
UnivariateTimeTypeToContinuous
```

単一変数トランスフォーマーを構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいて時間型データの連続表現を作成し、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
UnivariateTimeTypeToContinuous = @load UnivariateTimeTypeToContinuous pkg=MLJModels
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = UnivariateTimeTypeToContinuous()`を実行します。ハイパーパラメータのデフォルトを上書きするには、`UnivariateTimeTypeToContinuous(zero_time=...)`のようにキーワード引数を提供します。

このモデルを使用して、`TimeType`要素型を持つベクターを`Float64`型（`Continuous`要素スカイタイプ）のベクターに変換します。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, x)
```

ここで

  * `x`: 要素型が`Dates.TimeType`のサブタイプである任意の抽象ベクター

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `zero_time`: 変換の下で0.0に対応する時間で、型はトレーニングデータの要素型と一致します。指定しない場合、トレーニング中に遭遇した最も早い時間が使用されます。
  * `step::Period=Hour(24)`: 変換の下で1単位に対応する時間間隔

# 操作

  * `transform(mach, xnew)`: `mach`がフィットしたときに推測されたエンコーディングを適用します

# フィッティングされたパラメータ

`fitted_params(mach).fitresult`は、実際に変換に使用されるタプル`(zero_time, step)`であり、ユーザーが指定したハイパーパラメータとは異なる場合があります。

# 例

```
using MLJ
using Dates

x = [Date(2001, 1, 1) + Day(i) for i in 0:4]

encoder = UnivariateTimeTypeToContinuous(zero_time=Date(2000, 1, 1),
                                         step=Week(1))

mach = machine(encoder, x)
fit!(mach)
julia> transform(mach, x)
5-element Vector{Float64}:
 52.285714285714285
 52.42857142857143
 52.57142857142857
 52.714285714285715
 52.857142
```
