```
simulateSE(fmu, instance=nothing, tspan=nothing; kwargs...)
simulateSE(fmu, tspan; kwargs...)
simulateSE(instance, tspan; kwargs...)
```

実装予定 ...

# 引数

  * `fmu::FMU3`: シミュレーションするFMU。注意: SEはFMI3でのみ利用可能です。
  * `c::Union{FMU3Instance, Nothing}=nothing`: FMUのインスタンス（FMI3）、利用できない場合は`nothing`。
  * `tspan::Union{Tuple{Float64, Float64}, Nothing}=nothing`: シミュレーション時間範囲をタプルとして指定（デフォルト = nothing: FMUのモデル記述からのデフォルト値を使用するか、指定されていない場合は(0.0, 1.0)）。

# キーワード引数

  * 実装予定 ...

# 戻り値:

  * [`FMUSolution`](@ref) 構造体。

他に[`simulate`](@ref)、[`simulateME`](@ref)、[`simulateCS`](@ref)も参照してください。
