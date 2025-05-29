```
抽象型 LinSolver
```

この型から継承された構造体は、特定の `λ` 値に関連する NEP に関連する線形システムを解くことができます。最も一般的なのは、[`FactorizeLinSolver`](@ref)、[`BackslashLinSolver`](@ref) のような直接ソルバーや、[`GMRESLinSolver`](@ref) のような反復ソルバーです。

LinSolver オブジェクトは通常、NEP アルゴリズムによって作成者関数を通じて作成され、パラメータとして渡されます。

# 例

最も一般的な使用例は、`linsolvercreator` 関数を NEP アルゴリズムにパラメータとして渡したい場合です。この例では、バックスラッシュまたは `factorize()` に基づくソルバーを使用する方法を示します。この例では、`BackslashLinSolver` はシステム行列がアルゴリズム全体で同じであることを利用せず、したがって遅くなります。

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> using BenchmarkTools
julia> v0=ones(size(nep,1));
julia> @btime λ,v=quasinewton(nep,λ=-1,v=v0, linsolvercreator=DefaultLinSolverCreator());
  181.017 ms (3779 allocations: 58.61 MiB)
julia> @btime λ,v=quasinewton(nep,λ=-1,v=v0, linsolvercreator=BackslashLinSolverCreator());
  2.040 s (4510 allocations: 553.24 MiB)
```

# 例

`LinSolver` は拡張性のために構築されています。この例では、NEP が 2x2 の次元を持つ場合に逆行列の明示的な式を使用する独自の `LinSolver` を作成します。

型と作成者を作成します。

```julia
julia> using LinearAlgebra
julia> struct MyLinSolver <: LinSolver
   M::Matrix{ComplexF64}
end
julia> function my_linsolvercreator(nep,λ)
   M=compute_Mder(nep,λ);
   return MyLinSolver(M);
end
```

線形システムを解く方法を示すために `lin_solve` を明示的にインポートします。

```julia-repl
julia> import NonlinearEigenproblems.LinSolvers.lin_solve;
julia> function lin_solve(solver::MyLinSolver,b::AbstractVecOrMat;tol=0)
   M=solver.M;
   invM=(1/(det(M)))*[M[2,2] -M[1,2];-M[2,1] M[1,1]]
   return invM*b
end
julia> nep=SPMF_NEP([[1.0 3.0; 4.0 5.0], [2.0 1.0; -1 2.0]], [S->S^2,S->exp(S)])
julia> λ,v=quasinewton(nep,λ=-1,v=[1;1],linsolvercreator=my_linsolvercreator);
```

参照: [`lin_solve`](@ref), [`FactorizeLinSolver`](@ref), [`FactorizeLinSolver`](@ref), [`DefaultLinSolverCreator`](@ref), [`BackslashLinSolver`](@ref), [`BackslashLinSolverCreator`](@ref), [`GMRESLinSolver`](@ref), [`GMRESLinSolverCreator`](@ref)
