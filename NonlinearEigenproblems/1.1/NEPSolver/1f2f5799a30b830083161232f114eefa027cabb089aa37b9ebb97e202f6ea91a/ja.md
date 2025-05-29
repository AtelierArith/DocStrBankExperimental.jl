```
 mslp([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][logger,][eigsolvertype::Type])
```

連続線形問題の手法を実行します。この手法は、各反復で一般化固有値問題の解決を必要とします。固有値計算に使用される手法は、eigsolvertypeで指定されます。他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

[`SPMF_NEP`](@ref)を使用して有理NEPを作成します。

```julia-repl
julia> eye=Matrix{Float64}(I,3,3);
julia> Av=[ones(3,3),eye,triu(ones(3,3))];
julia> fv=[S-> S, S -> S^2, S->inv(S-one(S)*10)];
julia> nep=SPMF_NEP(Av,fv);
julia> (λ,v)=mslp(nep);
julia> compute_Mlincomb(nep,λ,v)
3-element Array{Complex{Float64},1}:
 -1.38778e-17+1.65715e-18im
 -5.55112e-17+1.30633e-17im
 -4.16334e-17-1.54436e-17im
```

# 参考文献

  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689
