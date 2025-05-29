```julia
HookStiffnessOperator1D(
    μ;
    name,
    regions,
    ∇,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

与えられたμに対する1D剛性テンソルCに対して、a(u,v) = (μ ∇u,∇v)となるバイリニア形式のコンストラクタ。
