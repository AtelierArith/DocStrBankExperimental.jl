```
dnep=deflate_eigpair(orgnep::NEP,λ,v,[mode=:Auto])
```

This function creates a deflated NEP based on $(λ,v)$, which are assumed to an eigenpair of `nep`. Effectively, the function will return `dnep::NEP` which has the same solutions as orgnep, except those corresponding to $(λ,v)$. Deflation is typically used to avoid reconvergence.

If `orgnep` is a `DeflatedNEP`, the `orgnep` the deflation in `orgnep` will be updated.

The `mode` kwarg can be `:Auto`, `:Generic`, `:SPMF`, `:MM`. This specifies how the deflated NEP should be represented. Which mode is the most efficient depends on many problem properties. If the original NEP is an `AbstractSPMF` with only a few terms, `mode=:SPMF` may be efficient. The SPMF-mode is based on a diagonalization of the deflated invariant pair and is not necessarily robust when you deflate eigenvalues near to each other. When `mode=:MM` is used, all compute functions are implemented via calls to the `compute_MM`. This can work well for small dense problems. The `:Generic` is based on an explicit derivation of the problem (via binomial expansion) which can be efficient if low order derivates are needed. If `:Auto` is selected, NEP-PACK tries to determine which one is the most efficient based on the `orgnep`.

# Example:

```julia-repl
julia> nep=nep_gallery("dep0");
julia> (λ,v)=newton(nep,v=ones(size(nep,1)));
julia> dnep=deflate_eigpair(nep,λ,v)
julia> (λ2,v2)=augnewton(dnep,v=ones(size(dnep,1)));  # this converges to different eigval
julia> using LinearAlgebra;
julia> minimum(svdvals(compute_Mder(nep,λ2)))
2.5161012836775824e-17
```

The function [`get_deflated_eigpairs()`](@ref) extracts the eigenpairs that have been deflated. The returned pairs are eigenpairs of the original NEP:

```julia-repl
julia> dnep=deflate_eigpair(dnep,λ2,v2);
julia> (D,V)=get_deflated_eigpairs(dnep)
julia> norm(compute_Mlincomb(nep,D[1],V[:,1]))
2.3970746442479104e-16
julia> norm(compute_Mlincomb(nep,D[2],V[:,2]))
8.101585801848734e-16
```

# References

  * C. Effenberger, Robust solution methods for nonlinear eigenvalue problems, PhD thesis, 2013, EPF Lausanne
