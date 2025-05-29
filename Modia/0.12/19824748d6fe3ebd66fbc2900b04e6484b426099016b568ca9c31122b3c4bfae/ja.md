```
signal    = get_result(instantiatedModel, name; unit=true)
dataFrame = get_result(instantiatedModel; onlyStates=false, extraNames=missing)
```

  * 最初の形式: `instantiatedModel`のシミュレーションが成功した後、信号`name::String`の結果をポイントのベクトルとして、その単位と共に返します。時間ベクトルのパス名は`"time"`です。`unit=false`の場合、信号は**単位なし**で返されます。
  * 2番目の形式: DataFrameオブジェクトの形式で**完全な結果**を返します。したがって、パッケージ[DataFrames](https://dataframes.juliadata.org/stable/)の全機能を使用でき、異なる形式でファイルに結果を保存することができます。DataFrameオブジェクトにはスカラーVar(..)変数のみが含まれます。`onlyStates=true`の場合、状態と`extraNames::Vector{String}`で識別された信号のみが`dataFrame`に保存されます。`onlyStates=false`で`extraNames`が指定された場合、`dataFrame`には`extraNames`で識別された信号のみが保存されます。

# 例

```julia
using Modia
@usingModiaPlot
using Unitful

include("$(Modia.path)/examples/Pendulum.jl")
using  .Model_Pendulum

pendulum = simulationModel(Pendulum)
simulate!(pendulum, stopTime=7.0)

# 結果から1つの信号を取得し、希望のプロットパッケージでプロット
time = get_result(pendulum, "time")  # 単位u"s"のベクトル
phi  = get_result(pendulum, "phi")   # 単位u"rad"のベクトル

import PyPlot
PyPlot.figure(4)   # 図4に変更（存在しない場合は作成）
PyPlot.clf()       # 現在の図をクリア
PyPlot.plot(stripUnit(time), stripUnit(phi), "b--", label="phi in " * string(unit(phi[1])))
PyPlot.xlabel("time in " * string(unit(time[1])))
PyPlot.legend()

# 完全な結果を取得し、1つの信号をプロット
result = get_result(pendulum)
plot(result, "phi")

# 参照として使用するために状態のみを取得し、結果を参照と比較
reference = get_result(pendulum, onlyStates=true)
(success, diff, diff_names, max_error, within_tolerance) =
    SignalTables.compareResults(result, reference, tolerance=0.01)
println("結果を確認: success = success")
```
