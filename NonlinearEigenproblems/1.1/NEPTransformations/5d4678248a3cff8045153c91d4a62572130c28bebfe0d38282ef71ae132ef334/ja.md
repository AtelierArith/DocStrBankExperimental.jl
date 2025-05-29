```
cplr=lowRankCompress(cp_org::CORKPencil,dtilde,rk)
```

[`CORKPencilLR`](@ref)を[`CORKPencil`](@ref)から構築します。これは、`dtilde`より高い項が低ランクであり、ランク`rk`であると仮定することによって行われます。より正確には、すべての`A[j]`および`B[j]`（`j>dtilde`の場合）は、$C_jZ^T$の形であると仮定されます。

# 例

これは、NEPから`CORKPencil`を形成し、その後`CORKPencilLR`を使用してより小さなペンシルを形成する方法を示しています。

```julia-repl
julia> A0=[1.0 3.0; -1.0 2.0]/10;
julia> v=[-1.0 ; 1]/sqrt(2);
julia> nep=DEP([A0,v*v']);
julia> cp_org=CORKPencil(nep,IarCorkLinearization(d=10));
julia> cplr=lowRankCompress(cp_org::CORKPencil,1,1);
julia> (AA,BB)=buildPencil(cplr);
julia> λ=eigen(AA,BB).values[end];
julia> minimum(svdvals(A0-λ*I+v*v'*exp(-λ))) # 固有値であるか確認
2.7621446071952216e-14
```
