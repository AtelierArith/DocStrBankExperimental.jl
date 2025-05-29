```
abstract type EigSolver
```

Structs inheriting from this type are able to solve linear eigenvalue problems arising in certain methods, such as, e.g., `mslp`, `sgiter`, and `polyeig`.

The `EigSolver` objects are passed as types to the NEP-algorithms, which uses it to dispatch the correct version of the function [`eig_solve`](@ref).

# Example

The most common usecase is that you do not want to specify anything in particular, since the [`DefaultEigSolver`](@ref) will use a dense or a sparse method depending on you problem. However, this example shows how you can force `mslp` to use the sparse solver.

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> λ,v = mslp(nep, eigsolvertype=ArnoldiEigSolver);
julia> norm(compute_Mlincomb(nep,λ,v))
9.323110647141726e-16
```

# Example

The `EigSolver`s are constructed for extendability. As an illustartion this example creates a naive `EigSolver` which casts the problem to a standard linear eigenproblem and calls the built-in function to solve it.

Create the types and a creator.

```julia-repl
julia> struct MyEigSolver <: EigSolver
   A
   E
   function MyEigSolver(A,E)
      return new(A,E)
   end
end

julia> import NonlinearEigenproblems.LinSolvers.eig_solve;
julia> function eig_solve(solver::MyEigSolver;nev = 1, target = 0)
   M = solver.E \ solver.A
   eig = eigen(M)
   i = argmin(abs.(eig.values))
   return eig.values[i], eig.vectors[:,i]
end
julia> nep=nep_gallery("dep0", 50);
julia> λ,v = mslp(nep, eigsolvertype=MyEigSolver, tol=1e-5);
julia> norm(compute_Mlincomb(nep,λ,v))
3.0777795031319117e-10
```

See also: [`eig_solve`](@ref), [`DefaultEigSolver`](@ref), [`EigenEigSolver`](@ref), [`ArnoldiEigSolver`](@ref), [`eig_solve`](@ref)
