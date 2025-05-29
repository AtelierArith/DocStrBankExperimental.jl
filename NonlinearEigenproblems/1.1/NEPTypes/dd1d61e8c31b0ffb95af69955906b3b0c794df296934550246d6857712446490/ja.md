```
expand_projectmatrices!(nep::Proj_SPMF_NEP, Wnew, Vnew)
```

投影された NEP は、`Wnew` と `Vnew` の最後の列を基底に追加することで更新されます。`Wnew` と `Vnew` には「古い」基底ベクトルも含まれていることに注意してください。詳細は [`create_proj_NEP`](@ref) を参照してください。

# 例:

以下の例では、拡張された投影問題が1行1列多くなり、先頭のサブブロックは小さい投影 NEP と同じであることがわかります。

```julia-repl
julia> nep=nep_gallery("pep0"); n=size(nep,1);
julia> V=Matrix(1.0*I,n,2); W=Matrix(1.0*I,n,2);
julia> pnep=create_proj_NEP(nep);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,0)
2×2 Array{Complex{Float64},2}:
 0.679107+0.0im   -0.50376+0.0im
 0.828413+0.0im  0.0646768+0.0im
julia> Vnew=[V ones(n)]
julia> Wnew=[W ones(n)]
julia> expand_projectmatrices!(pnep,Wnew,Vnew);
julia> compute_Mder(pnep,0)
3×3 Array{Complex{Float64},2}:
 0.679107+0.0im   -0.50376+0.0im  -12.1418+0.0im
 0.828413+0.0im  0.0646768+0.0im   16.3126+0.0im
 -17.1619+0.0im   -10.1628+0.0im   48.9481+0.0im
```
