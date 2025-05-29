```julia
solve(nls::AbstractNLS,
      θ_init::AbstractVector,
      conf::Abstract_Solver_Conf)::Abstract_Solver_Result
```

[`AbstractNLS`](@ref) 問題を解くための汎用インターフェースです。

使用されるアルゴリズムは [`Abstract_Solver_Conf`](@ref) の特化によって定義されます。

このメソッドは [`Abstract_Solver_Result`](@ref) の特化を返します。
