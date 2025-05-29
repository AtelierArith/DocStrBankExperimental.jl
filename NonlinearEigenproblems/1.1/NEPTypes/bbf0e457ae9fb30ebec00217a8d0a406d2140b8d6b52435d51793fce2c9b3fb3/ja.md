```
pnep=create_proj_NEP(orgnep::ProjectableNEP[,maxsize [,T]])
```

投影された問題を表すNEPを作成します $N(λ)=W^HM(λ)V$、ここで基本NEPは`orgnep`によって表されます。オプションのパラメータ`maxsize::Int`は、投影された問題の最大サイズを決定し、`T`は投影行列に使用される数値型です（デフォルトは`ComplexF64`）。これはメモリの事前割り当ての理由で必要です。投影行列$V$と$W$を指定するには、[`set_projectmatrices!`](@ref)および[`expand_projectmatrices!`](@ref)を使用します。

# 例:

以下の例は、`NEP`の投影が別の`NEP`であることを示しており、例えば`compute_Mder`を呼び出すことができます:

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
julia> W'*compute_Mder(nep,3.0)*V  # 同じ結果を返します
2×2 Array{Float64,2}:
 6.08082   -5.47481
 0.986559  -6.98165
```

実数の投影行列のみを使用することがわかっている場合は、作成時にこれを指定できます:

```julia-repl
julia> pnep=create_proj_NEP(nep,2,Float64);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,3.0)
2×2 Array{Float64,2}:
 6.08082   -5.47481
 0.986559  -6.98165
```
