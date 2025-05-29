```
SumNEP{nep1::NEP,nep2::NEP}
SumNEP{nep1::AbstractSPMF,nep2::AbstractSPMF}
```

`SumNEP` is a function creating an object that corresponds to a sum of two NEPs, i.e., if nep is created by `SumNEP` it is defined by

$$
M(λ)=M_1(λ)+M_2(λ)
$$

where $M_1$ and $M_2$ are defined by `nep1` and `nep2`.

# Example:

```julia-repl
julia> nep1=DEP([ones(3,3),randn(3,3)])
julia> nep2=PEP([ones(3,3),randn(3,3),randn(3,3)])
julia> sumnep=SumNEP(nep1,nep2);
julia> s=3.0;
julia> M=compute_Mder(sumnep,s);
3×3 Array{Float64,2}:
  8.54014     6.71897   7.12007
 -0.943908  -13.0795   -0.621659
  6.03155    -7.26726  -6.42828
julia> M1=compute_Mder(nep1,s);
julia> M2=compute_Mder(nep2,s);
julia> M1+M2  # Same as M
3×3 Array{Float64,2}:
  8.54014     6.71897   7.12007
 -0.943908  -13.0795   -0.621659
  6.03155    -7.26726  -6.42828
```

See also: [`SPMFSumNEP`](@ref), [`GenericSumNEP`](@ref)
