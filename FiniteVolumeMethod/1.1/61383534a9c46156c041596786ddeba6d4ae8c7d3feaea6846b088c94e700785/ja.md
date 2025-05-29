```
FVMProblem(mesh, boundary_conditions[, internal_conditions];
    diffusion_function=nothing,
    diffusion_parameters=nothing,
    source_function=nothing,
    source_parameters=nothing,
    flux_function=nothing,
    flux_parameters=nothing,
    initial_condition,
    initial_time=0.0,
    final_time)
```

`FVMProblem`を構築します。詳細は[`FVMSystem`](@ref)および[`SteadyFVMProblem`](@ref)を参照してください。

# 引数

  * `mesh::FVMGeometry`

PDEが定義されるメッシュで、[`FVMGeometry`](@ref)として与えられます。

  * `boundary_conditions::BoundaryConditions`

PDEの境界条件で、[`BoundaryConditions`](@ref)として与えられます。

  * `internal_conditions::InternalConditions=InternalConditions()`

PDEの内部条件で、[`InternalConditions`](@ref)として与えられます。この引数はオプションです。

# キーワード引数

  * `diffusion_function=nothing`

`isnothing(flux_function)`の場合、拡散源の定式化を提供するためにこれを指定できます。詳細は[`construct_flux_function`](@ref)を参照してください。形式は`D(x, y, t, u, p)`である必要があります。

  * `diffusion_parameters=nothing`

`diffusion_function`の引数`p`。

  * `source_function=(x, y, t, u, p) -> zero(u)`

ソース項で、形式は`S(x, y, t, u, p)`です。

  * `source_parameters=nothing`

`source_function`の引数`p`。

  * `flux_function=nothing`

フラックス関数で、形式は`q(x, y, t, α, β, γ, p) ↦ (qx, qy)`です。ここで、`(qx, qy)`はフラックスベクトルで、`(α, β, γ)`は`u ≈ αx+βy+γ`を推定するための形状関数係数です。`isnothing(flux_function)`の場合、代わりに`diffusion_function`が使用されて関数が構築されます。

  * `flux_parameters=nothing`

`flux_function`の引数`p`。

  * `initial_condition`

初期条件で、`initial_condition[i]`は`mesh`の`i`番目のノードでの初期値です。

  * `initial_time=0.0`

初期時間。

  * `final_time`

最終時間。

# 出力

返される値は対応する[`FVMProblem`](@ref)構造体です。その後、DifferentialEquations.jlの[`solve(::Union{FVMProblem,FVMSystem}, ::Any; kwargs...)`](@ref)を使用して問題を解決できます。
