```
pnep=create_proj_NEP(orgnep::ProjectableNEP[,maxsize [,T]])
```

Create a NEP representing a projected problem $N(λ)=W^HM(λ)V$,  where the base NEP is represented by `orgnep`. The optional parameter `maxsize::Int` determines how large the projected problem can be and `T` is the Number type used for the projection matrices (default `ComplexF64`). These are needed for memory preallocation reasons. Use [`set_projectmatrices!`](@ref) and [`expand_projectmatrices!`](@ref)  to specify projection matrices $V$ and $W$.

# Example:

The following example illustrates that a projection of a `NEP` is also a `NEP` and we can for instance call `compute_Mder` on it:

```julia-repl
julia> nep=nep_gallery("pep0")
julia> V=Matrix(1.0*I,size(nep,1),2);
julia> W=Matrix(1.0*I,size(nep,1),2);
julia> pnep=create_proj_NEP(nep);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,3.0)
2×2 Array{Complex{Float64},2}:
  6.08082+0.0im  -5.47481+0.0im
 0.986559+0.0im  -6.98165+0.0im
julia> W'*compute_Mder(nep,3.0)*V  # Gives the same result
2×2 Array{Float64,2}:
 6.08082   -5.47481
 0.986559  -6.98165
```

If you know that you will only use real projection matrices, you can specify this in at the creation:

```julia-repl
julia> pnep=create_proj_NEP(nep,2,Float64);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,3.0)
2×2 Array{Float64,2}:
 6.08082   -5.47481
 0.986559  -6.98165
```
