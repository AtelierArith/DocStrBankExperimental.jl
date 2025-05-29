```
(A, finalStates) = linearize!(instantiatedModel [, algorithm];
                              stopTime = 0.0,
                              analytic = false,
                              <all other keyword arguments of simulate!>)
```

`stopTime`までシミュレーションを行い、`finalStates`で`instantiatedModel`を線形化します。状態ベクトルの名前は`get_xNames(instantiatedModel)`で照会できます。

デフォルトでは、線形化はパッケージ[FiniteDiff](https://github.com/JuliaDiff/FiniteDiff.jl)を使用して中央差分近似で数値的に行われます。`analytic = true`を設定すると、線形化はパッケージ[ForwardDiff](https://github.com/JuliaDiff/ForwardDiff.jl)を使用して解析的に行われ、モデルを記号的に微分することによって計算されます。`ForwardDiff`は、`Measurements`のような一部の浮動小数点型と互換性がない場合があり、その場合、Juliaは一部のオーバーロードされた操作が曖昧であるというエラーをトリガーします。したがって、そのような場合には`analytic=true`は機能しません。

解析的線形化は、行列`A`をフル精度で返しますが、数値的線形化は`A`を減少精度で返します（FloatType = Float64の場合、解析的線形化は約15桁の正確な数字を結果として生成し、数値的線形化は約10桁の正確な数字を生成します）。この状況を改善するには、これが重要な場合に`instantiatedModel`に対してより大きな`FloatType`を使用することができます（以下の例を参照）。

# 出力引数

  * `A::Matrix`: 線形ODEの行列A: $\Delta \dot{x} = A*\Delta x$。
  * `finalStates::Vector`: 線形化点。

# 例

```julia
using ModiaLang
using DoubleFloats
using Measurements

FirstOrder = Model(
    T = 0.4 ± 0.04,
    x = Var(init = 0.9 ± 0.09),
    equations = :[u = inputSignal(time/u"s"),
                  T * der(x) + x = u]
)

firstOrder1 = @instantiateModel(FirstOrder, FloatType = Measurement{Float64})

# 標準精度
(A1, finalStates1) = linearize!(firstOrder1)

# 高精度
firstOrder2 = SimulationModel{Measurement{Double64}}(firstOrder1)
(A2, finalStates2) = linearize!(firstOrder2)

# 15桁で結果を表示（Measurementsのデフォルトの印刷は3桁を表示）
println(IOContext(stdout, :error_digits=>15), "A1 = ", A1)
println(IOContext(stdout, :error_digits=>15), "A2 = ", A2)
```
