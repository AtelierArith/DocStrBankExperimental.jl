```
λv,V,U=infbilanczos([eltype],nep, nept,[linsolvecreator,][linsolvertcreator,][v,][u,][σ,][γ,][tol,][neigs,][errmeasure,][logger,][maxit,][check_error_every])
```

`nep::NEP` と `nept::NEP` で定義された問題に対して無限バイランチョス法を実行します。`nep:NEP` は元の非線形固有値問題であり、`nept::NEP` はその（エルミート）転置です: $M(λ^*)^H$。`v` と `u` は開始ベクトルで、`σ` はシフト、`γ` はスケーリングです。反復は `neigs` リッツ対が収束するまで続けられます。この関数は、`maxit` 回の反復後に求められた固有対が計算されない場合、`NoConvergenceException` をスローします。ただし、`neigs` が `Inf` に設定されている場合、エラーがスローされることなく `maxit` 回の反復が続けられます。他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例:

```julia-repl
julia> nep=nep_gallery("dep0");
julia> A=get_Av(nep); fv=get_fv(nep);
julia> At=[copy(A[1]'),copy(A[2]'),copy(A[3]')]
julia> nept=SPMF_NEP(At,fv); # 転置されたNEPを作成
julia> λv,V=infbilanczos(nep,nept,neigs=3,v=ones(size(nep,1)))
julia> norm(compute_Mlincomb(nep,λv[1],V[:,1]))
9.907299130783851e-15
```

# 参考文献:

  * 非線形固有値問題のための無限バイランチョス法, S. W. Gaaf と E. Jarlebring, SIAM J. Sci. Comput. 39:S898-S919, 2017, [プレプリント](https://arxiv.org/abs/1607.03454)
