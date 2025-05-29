```
λ,v = newton([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][armijo_factor=1,][armijo_max])
```

非線形方程系に対してニュートン・ラフソン法を適用します。未知数は `n+1` 個です：

$$
M(λ)v=0
$$

$$
c^Hv-1=0
$$

ベクトル `c` は直交化ベクトルです。`c=0` の場合、現在の近似値が直交化に使用されます。他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

```julia-repl
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> λ,v=newton(nep);
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.9997125567227177e-16
```

# 参考文献

  * Nichtlineare Behandlung von Eigenwertaufgaben, Z. Angew. Math. Mech. 30 (1950) 281-282.
  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689

```
