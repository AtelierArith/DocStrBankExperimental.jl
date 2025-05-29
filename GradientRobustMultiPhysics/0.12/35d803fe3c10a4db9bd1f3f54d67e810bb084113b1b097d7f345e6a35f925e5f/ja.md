```julia
LaplaceOperator(
;
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, SymmetricBilinearForm, ON_CELLS}
LaplaceOperator(
    κ;
    name,
    AT,
    ∇,
    regions,
    store
) -> Union{Nothing, GradientRobustMultiPhysics.PDEOperator{Float64, SymmetricBilinearForm, ON_CELLS}}

```

双線形形式を記述するためのコンストラクタ a(u,v) = κ (∇u,∇v) であり、κは定数（拡散）係数です。
