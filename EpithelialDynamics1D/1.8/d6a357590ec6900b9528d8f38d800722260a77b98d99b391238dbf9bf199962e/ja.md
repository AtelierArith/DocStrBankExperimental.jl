```
node_densities(sol::EnsembleSolution;
    indices=eachindex(sol),
    num_knots=500,
    stat=(minimum, maximum),
    knots=get_knots(sol, num_knots; indices, stat),
    alpha=0.05,
    interp_fnc=(u, t) -> LinearInterpolation{true}(u, t),
    smooth_boundary=true)
```

`EnsembleSolution`からのノード密度の要約統計を計算します [`CellProblem`](@ref)。負の値はゼロに設定されます。

# 引数

  * `sol::EnsembleSolution`: `CellProblem`に対するアンサンブルソリューション。

# キーワード引数

  * `indices = eachindex(sol)`: 考慮するセルシミュレーションのインデックス。
  * `num_knots::Int = 500`: スプライン補間に使用するノットの数。
  * `stat = (minimum, maximum)`: `get_knots`のためにノットを要約する方法。
  * `parallel = false`: ループにマルチスレッドを使用するかどうか。
  * `knots::Vector{Vector{Float64}} = get_knots(sol, num_knots; indices, stat, parallel)`: スプライン補間に使用するノット。
  * `alpha::Float64 = 0.05`: 信頼区間の有意水準。
  * `interp_fnc = (u, t) -> LinearInterpolation{true}(u, t)`: 補間関数を構築するために使用する関数。
  * `smooth_boundary::Bool = true`: スムーズな境界ノード密度を使用するかどうか。
  * `extrapolate = false`: 特定の時間と特定のシミュレーションのためにセルの範囲外を評価する際に外挿を許可するかどうか。

# 出力

  * `q::Vector{Vector{Vector{Float64}}}`: 各セルシミュレーションのノード密度。
  * `r::Vector{Vector{Vector{Float64}}}`: 各セルシミュレーションのセル位置。
  * `means::Vector{Vector{Float64}}`: 各セルシミュレーションの平均ノード密度。
  * `lowers::Vector{Vector{Float64}}`: 各セルシミュレーションのノード密度の信頼区間の下限。
  * `uppers::Vector{Vector{Float64}}`: 各セルシミュレーションのノード密度の信頼区間の上限。
  * `knots::Vector{Vector{Float64}}`: スプライン補間に使用されるノット。
