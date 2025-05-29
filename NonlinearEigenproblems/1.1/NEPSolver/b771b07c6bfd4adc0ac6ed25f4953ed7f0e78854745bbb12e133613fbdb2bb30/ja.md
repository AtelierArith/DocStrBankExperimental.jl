```
rfi(nep,nept,[λ=0,][errmeasure,][tol=eps()*100,][maxit=100,][v=randn,][u=randn,][logger=0,][linsolvecreator=DefaultLinSolverCreator(),])
```

これは、`nep`で指定された問題の固有三重項を計算するための両側レイリー関数反復（RFI）の実装です。この方法では、`nept`で指定されたNEPの転置が必要です。`λ`、`u`、および`v`は、それぞれ固有値、右固有ベクトル、および左固有ベクトルの初期推定値です。他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("dep0");
julia> nept=DEP([nep.A[1]',nep.A[2]'])
julia> λ,v,u=rfi(nep,nept)
julia> compute_resnorm(nep,λ,v) # vは右固有ベクトルです
3.0171586304599647e-16
julia> compute_resnorm(nept,λ,u) # uは右固有ベクトルです
7.145081514857076e-17
```

# 参考文献

  * Schreiber, Nonlinear Eigenvalue Problems: Newton-type Methods and Nonlinear Rayleigh Functionals, PhD thesis, TU Berlin, 2008のアルゴリズム4。
