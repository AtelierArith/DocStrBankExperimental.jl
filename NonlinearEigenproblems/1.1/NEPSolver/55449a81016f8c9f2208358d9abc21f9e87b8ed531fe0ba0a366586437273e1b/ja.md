```
function nlar([eltype],nep::ProjectableNEP,[orthmethod=ModifiedGramSchmidt()],[neigs=10],[errmeasure],[tol=eps(real(T))*100],[maxit=100],[0=0],[v=randn(T,size(nep,1))],[logger=0],[linsolvercreator=DefaultLinSolverCreator()],[R=0.01],[eigval_sorter=residual_eigval_sorter],[qrfact_orth=false],[max_subspace=100],[num_restart_ritz_vecs=8],[inner_solver_method=DefaultInnerSolver(),][inner_logger=0])
```

この関数は非線形アーノルディ法を実装しており、`neigs` 個の固有対を見つける（または `NoConvergenceException` を投げる）ために、アルゴリズムの過程で拡張される部分空間に問題を投影します。基底は、`qrfact_orth` が `true` の場合は QR 法を使用して直交化され、それ以外の場合は `orthmethod` による直交化法が使用されます。これは、`inner_solver_method` によって指定された方法を使用して、より小さな投影問題を解くことを伴います。内部ソルバーのログは `inner_logger` によって決定され、これは `logger` と同様に機能します。(`λ`,`v`) は固有対の初期推定値です。`linsolvercreator` は線形システムがどのように作成され、解かれるかを指定します。`R` は、`eigval_sorter` によって指定された関数が収束した固有値からの距離 `R` 内にあるリッツ値を拒否するために使用されるパラメータであり、同じ固有対への繰り返し収束を避けることができます。`max_subspace` は、アルゴリズムが `num_restart_ritz_vecs` リッツベクトルとアルゴリズムが収束した固有ベクトルからなる基底を使用して再起動する前の基底の最大許容サイズです。

他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("dep0_tridiag");
julia> λ,v=nlar(nep,tol=1e-7,neigs=1,maxit=100,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ[1],v))
8.00192341259751e-7
```

# 参考文献

  * H. Voss, An Arnoldi method for nonlinear eigenvalue problems. BIT. Numer. Math. 44: 387-401, 2004.

```
