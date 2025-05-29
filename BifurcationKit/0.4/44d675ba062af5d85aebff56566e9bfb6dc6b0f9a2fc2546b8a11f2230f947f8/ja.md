```julia
struct MatrixBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}} <: BifurcationKit.AbstractBorderedLinearSolver
```

この構造体は、全行列を反転させることに基づいて境界付き線形ソルバーを提供するために使用されます。

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: 全行列を反転させるために使用される線形ソルバー。
