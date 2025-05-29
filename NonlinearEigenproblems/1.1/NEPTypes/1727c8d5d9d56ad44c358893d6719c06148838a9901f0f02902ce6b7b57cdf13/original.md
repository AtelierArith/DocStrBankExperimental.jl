```
set_projectmatrices!(pnep::Proj_NEP,W,V)
```

Set the projection matrices for the NEP to `W` and `V`, i.e., corresponding the NEP: $N(λ)=W^HM(λ)V$. See also [`create_proj_NEP`](@ref).

# Example

This illustrates if `W` and `V` are vectors of ones, the projected problem becomes the sum of the rows and columns of the original NEP.

```julia-repl
julia> nep=nep_gallery("pep0")
julia> pnep=create_proj_NEP(nep);
julia> V=ones(200,1);  W=ones(200,1);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,0)
1×1 Array{Complex{Float64},2}:
 48.948104019482756 + 0.0im
julia> sum(compute_Mder(nep,0),dims=[1,2])
1×1 Array{Float64,2}:
 48.948104019482955
```
