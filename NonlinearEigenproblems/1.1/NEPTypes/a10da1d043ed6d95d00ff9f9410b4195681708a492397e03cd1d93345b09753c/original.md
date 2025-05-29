```
newspmf=DerSPMF(spmf,σ,m)
```

Creates a `DerSPMF` representing the NEP `spmf` where the first `m` derivatives of the functions `f_i` in the number `σ` are precomputed. This will in general speed up the execution of [`compute_Mlincomb`](@ref) for the selected shift `σ`.

# Parameters

  * `spmf` is the original `AbstractSPMF`.
  * `σ::Number` specifies where the derivatives will be precomputed.

# Example

```julia-repl
julia> A0=[1 3; 4 5]; A1=[3 4; 5 6];
julia> id_op=S -> one(S) # Note: We use one(S) to be valid both for matrices and scalars
julia> exp_op=S -> exp(S)
julia> nep=SPMF_NEP([A0,A1],[id_op,exp_op]);
julia> m=5 # Precompute 5 derivatives
julia> σ=3.3
julia> dnep=DerSPMF(nep,σ,m)
julia> V=rand(2,m)
julia> z=compute_Mlincomb(dnep,σ,V)  # Same as below ...
2-element Array{Float64,1}:
39.47327945131233
64.31391434063991
julia> z=compute_Mlincomb(nep,σ,V)  # .. but more efficient
2-element Array{Complex{Float64},1}:
 381.008192939787 + 0.0im
 601.379183090249 + 0.0im
```
