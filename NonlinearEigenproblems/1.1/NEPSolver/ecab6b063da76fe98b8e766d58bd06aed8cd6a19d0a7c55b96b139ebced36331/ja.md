```
(S,X)=blocknewton(nep [S,] [X,] [errmeasure,] [tol,] [maxit,] [armijo_factor,] [armijo_max,] [logger])
```

ブロックニュートン法を `nep::AbstractSPMF` に適用します。この方法は、Kressnerのブロックニュートンアプローチを使用して不変ペア `(S,X)` を計算します。変数 `S`,`X` は開始近似に対応します。関数 `errmeasure` は errmeasure(S,X) のために定義され、ペア `(S,X)` の誤差を測定します。他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

この例では、解が計算されると `compute_MM()` がゼロになることを示しています。

```julia-repl
julia> nep=nep_gallery("dep0",3);
julia> (S,X)= blocknewton(nep)
julia> compute_MM(nep,S,X)
3×2 Array{Complex{Float64},2}:
 -1.11022e-16+0.0im  1.11022e-16+0.0im
          0.0+0.0im          0.0+0.0im
  1.38778e-17+0.0im  2.77556e-17+0.0im
```

この例は、ベルリン・マンチェスターコレクションからの `gun` 問題を解決します。

```julia-repl
julia> using NonlinearEigenproblems.Gallery
julia> nep=nep_gallery("nlevp_native_gun");
julia> II=[1.0 0; 0 1]; S=150^2*II; V=[II;zeros(size(nep,1)-2,2)];
julia> (Z,X)=blocknewton(nep,S=S,X=V,logger=1,armijo_factor=0.5,maxit=20)
Iteration 1: Error: 6.081316e+03
Iteration 2: Error: 1.701970e-02 Armijo scaling=0.031250
Iteration 3: Error: 1.814887e-02 Armijo scaling=0.250000
...
Iteration 13: Error: 6.257442e-09
Iteration 14: Error: 2.525942e-15
```

# 参考文献

  * D. Kressner A block Newton method for nonlinear eigenvalue problems, Numer. Math., 114 (2) (2009), pp. 355-372
