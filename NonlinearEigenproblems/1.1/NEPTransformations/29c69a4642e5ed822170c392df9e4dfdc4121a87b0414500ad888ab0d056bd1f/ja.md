```
struct CORKPencilLR
function CORKPencilLR(M,N,Av,AvLR,Bv,BvLR,Z);
```

低ランクのCORKペンシルを表現/構築します。`AvLR`、`BvLR`、および`Z`は、`Av`および`Bv`の低ランク因子分解に対応します。詳細は[`CORKPencil`](@ref)および以下の参考文献を参照してください。

# 例

この例は、NEP $A0-λI+vv^Te^{-λ}$のテイラー展開の低ランク線形化を示しています。

```julia-repl
julia> A0=[1.0 3.0; -1.0 2.0]/10;
julia> v=reshape([-1.0 ; 1]/sqrt(2),n,1);

julia> Av=[-A0-v*v']
julia> Bv=[-one(A0)-v*v']
julia> BvLR=[v/2, -v/3, v/4, -v/5, v/6, -v/7,  v/8, -v/9]
julia> AvLR=zero.(BvLR);
julia> Z=v;
julia> d=9;
julia> M=diagm( 0 =>  ones(d) )[2:end,:]
julia> N=diagm( -1 =>  1 ./ (1:d-1) )[2:end,:]
julia> cplr=CORKPencilLR(M,N,Av,AvLR,Bv,BvLR,Z);
julia> (AA,BB)=buildPencil(cplr);
julia> λ=eigen(AA,BB).values[end];
julia> minimum(svdvals(A0-λ*I+v*v'*exp(-λ)))
8.870165379112754e-13
```

# 参考文献:

  * 非線形固有値問題に対するコンパクトな有理Krylov法に関するセクション7 SIAM Journal on Matrix Analysis and Applications, 36 (2), 820-838, 2015.

```
