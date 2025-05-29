```julia
solve(nls::AbstractNLS,
      θ_init::AbstractVector,
      bc::BoundConstraints,
      conf::Abstract_BC_Solver_Conf) -> Abstract_Solver_Result
```

境界制約を持つ [`AbstractNLS`](@ref) 問題を解くための汎用インターフェースです。

使用されるアルゴリズムは [`Abstract_BC_Solver_Conf`](@ref) の特殊化を通じて定義されます。

このメソッドは [`Abstract_BC_Solver_Result`](@ref) の特殊化を返します。
