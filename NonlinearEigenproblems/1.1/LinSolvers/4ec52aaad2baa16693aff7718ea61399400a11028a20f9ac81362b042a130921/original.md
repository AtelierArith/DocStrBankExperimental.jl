```
abstract type LinSolver
```

Structs inheriting from this type are able to solve linear systems associated with a NEP, for a specific `λ`-value. The most common are direct solvers such as [`FactorizeLinSolver`](@ref), [`BackslashLinSolver`](@ref) and iterative solvers such as [`GMRESLinSolver`](@ref).

The LinSolver objects are usually created by the NEP-algorithms through creator functions, which are passed as parameters.

# Example

The most common usecase is that you want to pass a `linsolvercreator`-function as a parameter to the NEP-algorithm. This example shows how you can use solvers based on backslash or `factorize()`. In the example, `BackslashLinSolver` does not exploit that the system matrix remains the same throughout the algorithm and is therefore slower.

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> using BenchmarkTools
julia> v0=ones(size(nep,1));
julia> @btime λ,v=quasinewton(nep,λ=-1,v=v0, linsolvercreator=DefaultLinSolverCreator());
  181.017 ms (3779 allocations: 58.61 MiB)
julia> @btime λ,v=quasinewton(nep,λ=-1,v=v0, linsolvercreator=BackslashLinSolverCreator());
  2.040 s (4510 allocations: 553.24 MiB)
```

# Example

The `LinSolver`s are constructed for extendability. This example creates our own `LinSolver` which uses an explicit formula for the inverse if the NEP has dimension 2x2.

Create the types and a creator.

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

Explicit import `lin_solve` to show how to solve a linear system.

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

See also: [`lin_solve`](@ref), [`FactorizeLinSolver`](@ref), [`FactorizeLinSolver`](@ref), [`DefaultLinSolverCreator`](@ref), [`BackslashLinSolver`](@ref), [`BackslashLinSolverCreator`](@ref), [`GMRESLinSolver`](@ref), [`GMRESLinSolverCreator`](@ref)
