```
semidiscretize(semi, tspan; reset_threads=true)
```

指定された`tspan`を持つ半離散化から`ODEProblem`を作成します。

# 引数

  * `semi`: シミュレーションに関与するシステムを保持する[`Semidiscretization`](@ref)。
  * `tspan`: シミュレーションが実行される時間範囲。

# キーワード

  * `reset_threads`: シミュレーションの前にPolyester.jlスレッドをリセットするためのブールフラグ（デフォルト: `true`）。スレッド化されたループ内でエラーが発生した後、スレッドが無効になる可能性があります。シミュレーションの前にスレッドをリセットすることで、シミュレーションのために再度スレッドが有効になります。詳細は[trixi-framework/Trixi.jl#1583](https://github.com/trixi-framework/Trixi.jl/issues/1583)を参照してください。

# 戻り値

`DynamicalODEProblem`（[OrdinaryDiffEq.jlのドキュメント](https://docs.sciml.ai/DiffEqDocs/stable/types/dynamical_types/)を参照）で、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl)を使用して統合されます。これは、加速度が速度に依存しない真の`DynamicalODEProblem`ではないことに注意してください。したがって、`DynamicalODEProblem`用に設計されたすべての積分器が正しく動作するわけではありません。ただし、`ODEProblem`用に設計されたすべての積分器を使用できます。詳細については[時間積分](@ref time_integration)を参照してください。

# 例

```jldoctest; output = false, filter = r"u0: .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), sol=nothing); ref_system = fluid_system)
semi = Semidiscretization(fluid_system, boundary_system)
tspan = (0.0, 1.0)
ode_problem = semidiscretize(semi, tspan)

# output
ODEProblem with uType RecursiveArrayTools.ArrayPartition{Float64, Tuple{Vector{Float64}, Vector{Float64}}} and tType Float64. In-place: true
Non-trivial mass matrix: false
timespan: (0.0, 1.0)
u0: ([...], [...]) *この行はフィルタによって無視されます*
```
