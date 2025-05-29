```
abstract type InnerSolver
```

Structs inheriting from this type are used to solve inner problems in an inner-outer iteration.

The `InnerSolver` objects are passed to the NEP-algorithms, which uses it to dispatch the correct version of the function [`inner_solve`](@ref). Utilizes existing implementations of NEP-solvers and [`inner_solve`](@ref) acts as a wrapper to these.

# Example

There is a [`DefaultInnerSolver`](@ref) that dispatches an inner solver based on the provided NEP. However, this example shows how you can force [`nlar`](@ref) to use the [`IARInnerSolver`](@ref) for a PEP.

```julia-repl
julia> nep=nep_gallery("pep0", 100);
julia> λ,v = nlar(nep, inner_solver_method=NEPSolver.IARInnerSolver(), neigs=1, num_restart_ritz_vecs=1, maxit=70, tol=1e-8);
julia> norm(compute_Mlincomb(nep,λ[1],vec(v)))
8.68118417430353e-9
```

See also: [`inner_solve`](@ref), [`DefaultInnerSolver`](@ref), [`NewtonInnerSolver`](@ref), [`PolyeigInnerSolver`](@ref), [`IARInnerSolver`](@ref), [`IARChebInnerSolver`](@ref), [`SGIterInnerSolver`](@ref), [`ContourBeynInnerSolver`](@ref)
