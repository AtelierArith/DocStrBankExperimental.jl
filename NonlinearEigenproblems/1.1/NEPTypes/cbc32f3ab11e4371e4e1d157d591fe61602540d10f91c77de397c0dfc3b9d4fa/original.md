```
abstract ProjectableNEP <: NEP
```

A ProjectableNEP is a NEP which can be projected, i.e., one can construct the problem $W'*M(λ)Vw=0$ with the [`Proj_NEP`](@ref). A NEP which is of this must have the function [`create_proj_NEP(orgnep::ProjectableNEP)`](@ref) implemented. This function must return a `Proj_NEP`.

See also: [`set_projectmatrices!`](@ref).

# Example:

```julia-repl
julia> nep=nep_gallery("dep0");
julia> typeof(nep)
DEP{Float64,Array{Float64,2}}
julia> isa(nep,ProjectableNEP)
true
julia> projnep=create_proj_NEP(nep);
julia> e1 = Matrix(1.0*I,size(nep,1),1);
julia> set_projectmatrices!(projnep,e1,e1);
julia> compute_Mder(nep,3.0)[1,1]
-2.942777908030041
julia> compute_Mder(projnep,3.0)
1×1 Array{Complex{Float64},2}:
 -2.942777908030041 + 0.0im
```
