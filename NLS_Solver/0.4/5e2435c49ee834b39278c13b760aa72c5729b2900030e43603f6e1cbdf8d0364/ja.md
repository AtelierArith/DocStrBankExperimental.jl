```julia
abstract type Abstract_Solver_Result end
```

これは[`solve`](@ref)メソッドによって返される基本型です。見つかった解に関連する情報を含んでいます。

# インターフェース

  * [`converged`](@ref)
  * [`iteration_count`](@ref)
  * [`objective_value`](@ref)
  * [`solution`](@ref)

# 実装

  * [`LevenbergMarquardt_Result`](@ref)
  * [`LevenbergMarquardt_BC_Result`](@ref)
