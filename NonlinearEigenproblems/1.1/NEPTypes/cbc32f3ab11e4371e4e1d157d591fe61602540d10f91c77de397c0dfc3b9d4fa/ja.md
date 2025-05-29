```
abstract ProjectableNEP <: NEP
```

ProjectableNEPは、投影可能なNEPであり、すなわち、問題$W'*M(λ)Vw=0$を[`Proj_NEP`](@ref)を用いて構築することができます。このタイプのNEPは、関数[`create_proj_NEP(orgnep::ProjectableNEP)`](@ref)が実装されている必要があります。この関数は`Proj_NEP`を返さなければなりません。

関連情報: [`set_projectmatrices!`](@ref).

# 例:

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
