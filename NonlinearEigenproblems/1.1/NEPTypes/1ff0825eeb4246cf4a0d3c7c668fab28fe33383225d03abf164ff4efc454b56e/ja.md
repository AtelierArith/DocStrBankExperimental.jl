```
SumNEP{nep1::NEP,nep2::NEP}
SumNEP{nep1::AbstractSPMF,nep2::AbstractSPMF}
```

`SumNEP` は、2つの NEP の合計に対応するオブジェクトを作成する関数です。すなわち、`SumNEP` によって nep が作成されると、次のように定義されます。

$$
M(λ)=M_1(λ)+M_2(λ)
$$

ここで、$M_1$ と $M_2$ は `nep1` と `nep2` によって定義されます。

# 例:

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
julia> M1+M2  # M と同じ
3×3 Array{Float64,2}:
  8.54014     6.71897   7.12007
 -0.943908  -13.0795   -0.621659
  6.03155    -7.26726  -6.42828
```

参照: [`SPMFSumNEP`](@ref), [`GenericSumNEP`](@ref)
