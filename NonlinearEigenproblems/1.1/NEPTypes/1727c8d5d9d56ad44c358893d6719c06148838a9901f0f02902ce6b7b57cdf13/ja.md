```
set_projectmatrices!(pnep::Proj_NEP,W,V)
```

NEPの射影行列を`W`と`V`に設定します。すなわち、NEPに対応するのは、$N(λ)=W^HM(λ)V$です。詳細は[`create_proj_NEP`](@ref)を参照してください。

# 例

これは、`W`と`V`が1のベクトルである場合、射影された問題が元のNEPの行と列の合計になることを示しています。

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
