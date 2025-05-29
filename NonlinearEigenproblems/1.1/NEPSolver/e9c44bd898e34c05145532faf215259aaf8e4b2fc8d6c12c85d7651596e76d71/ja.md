```
quasinewton([T=ComplexF64],nep,[errmeasure,][tol,][maxit,][λ,][v][ws][logger][linsolvercreator,][armijo_factor,][armijo_max])
```

参照される準ニュートンアプローチの実装で、参考文献では準ニュートン2と呼ばれています。この手法は、$λ$が定数である場合に対応する行列$M(λ)$に対して、各反復ごとに1つの線形システムを解くことを含みます。ベクトル`ws`は正規化の表現であり、$c^T=w_s^TM(λ)$という意味で、すべての反復は$c^Tx_i=1$を満たします。その他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=quasinewton(nep,λ=1.0,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
5.448264607410413e-12
```

# 参考文献

  * Jarlebring, Koskela, Mele, Disguised and new Quasi-Newton methods for nonlinear eigenvalue problems, Numer. Algorithms, 79:311-335, 2018. [preprint](https://arxiv.org/abs/1702.08492)
