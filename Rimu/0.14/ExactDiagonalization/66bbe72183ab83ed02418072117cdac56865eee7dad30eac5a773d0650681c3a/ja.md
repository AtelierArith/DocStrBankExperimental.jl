```
LOBPCGSolver(; kwargs...)
```

局所最適ブロック前処理共役勾配法 (LOBPCG)。スパース行列をインスタンス化した後に [`ExactDiagonalizationProblem`](@ref) を解くためのアルゴリズムです。

LOBPCG は非エルミート固有値問題には適していません。

`kwargs` は関数 [`IterativeSolvers.lobpcg()`](https://iterativesolvers.julialinearalgebra.org/dev/eigenproblems/lobpcg/) に渡されます。

他に [`ExactDiagonalizationProblem`](@ref)、[`solve`](@ref solve(::ExactDiagonalizationProblem)) も参照してください。

!!! note
    `using IterativeSolvers` で IterativeSolvers.jl パッケージをロードする必要があります。

