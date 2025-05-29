```
cplr=lowRankCompress(cp_org::CORKPencil,dtilde,rk)
```

Constructs a [`CORKPencilLR`](@ref) from a [`CORKPencil`](@ref). This is done by assuming that terms higher than `dtilde` are of low rank, with rank `rk`. More precisely, all `A[j]` and `B[j]` for `j>dtilde` are assumed to be of the form $C_jZ^T$.

# Example

This illustrates how to form a `CORKPencil` from a NEP, and subsequently form a smaller pencil using `CORKPencilLR`.

```julia-repl
julia> A0=[1.0 3.0; -1.0 2.0]/10;
julia> v=[-1.0 ; 1]/sqrt(2);
julia> nep=DEP([A0,v*v']);
julia> cp_org=CORKPencil(nep,IarCorkLinearization(d=10));
julia> cplr=lowRankCompress(cp_org::CORKPencil,1,1);
julia> (AA,BB)=buildPencil(cplr);
julia> λ=eigen(AA,BB).values[end];
julia> minimum(svdvals(A0-λ*I+v*v'*exp(-λ))) # Check if it is an eigval
2.7621446071952216e-14
```
