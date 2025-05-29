```
λ,v = polyeig([eltype],nep::PEP,[eigsolvertype,])
```

Linearizes a  polynomial eigenvalue problem (PEP) a to the companion form and solves the corresponding linear eigenvalue problem; see [`companion`](@ref). The `eigsolvertype` is optinal can be used to specify how the linear problem is solved; see [`eig_solve`](@ref), and [`EigSolver`](@ref).

# Example

```julia-repl
julia> pep = nep_gallery("pep0");
julia> λ,V = polyeig(pep);
julia> minimum(svd(compute_Mder(pep,λ[1])).S)
1.2050763381899922e-14
julia> norm(compute_Mlincomb(pep,λ[2],vec(V[:,2])))
1.0245470569036458e-12
```
