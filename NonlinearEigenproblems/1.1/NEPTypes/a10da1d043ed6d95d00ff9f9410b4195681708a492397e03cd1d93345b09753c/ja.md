```
newspmf=DerSPMF(spmf,σ,m)
```

`spmf`を表す`DerSPMF`を作成します。ここで、最初の`m`の導関数が数`σ`の関数`f_i`に対して事前に計算されています。これは一般的に、選択したシフト`σ`に対する[`compute_Mlincomb`](@ref)の実行を高速化します。

# パラメータ

  * `spmf`は元の`AbstractSPMF`です。
  * `σ::Number`は導関数が事前に計算される場所を指定します。

# 例

```julia-repl
julia> A0=[1 3; 4 5]; A1=[3 4; 5 6];
julia> id_op=S -> one(S) # 注意: 行列とスカラーの両方に対して有効であるためにone(S)を使用します
julia> exp_op=S -> exp(S)
julia> nep=SPMF_NEP([A0,A1],[id_op,exp_op]);
julia> m=5 # 5つの導関数を事前に計算
julia> σ=3.3
julia> dnep=DerSPMF(nep,σ,m)
julia> V=rand(2,m)
julia> z=compute_Mlincomb(dnep,σ,V)  # 以下と同じ ...
2-element Array{Float64,1}:
39.47327945131233
64.31391434063991
julia> z=compute_Mlincomb(nep,σ,V)  # .. しかしより効率的
2-element Array{Complex{Float64},1}:
 381.008192939787 + 0.0im
 601.379183090249 + 0.0im
```
