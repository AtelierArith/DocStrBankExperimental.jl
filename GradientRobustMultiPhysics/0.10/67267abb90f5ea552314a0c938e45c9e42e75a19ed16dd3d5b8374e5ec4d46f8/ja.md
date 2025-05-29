```julia
HookStiffnessOperator1D(
    μ;
    name,
    regions,
    ∇,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

ビリニア形式 a(u,v) = (μ ∇u,∇v) のコンストラクタで、C は与えられた μ に対する 1D 剛性テンソルです。
