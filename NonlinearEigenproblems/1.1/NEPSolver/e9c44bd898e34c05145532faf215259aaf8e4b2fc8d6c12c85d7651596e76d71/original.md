```
quasinewton([T=ComplexF64],nep,[errmeasure,][tol,][maxit,][λ,][v][ws][logger][linsolvercreator,][armijo_factor,][armijo_max])
```

An implementation of the quasi-Newton approach referred to as quasi-Newton 2 in the reference. The method involves one linear system solve per iteration corresponding with the matrix $M(λ)$, where $λ$ is constant. The vector `ws` is a representation of the normalization, in the sense that $c^T=w_s^TM(λ)$, where all iterates satisfy $c^Tx_i=1$. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=quasinewton(nep,λ=1.0,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
5.448264607410413e-12
```

# References

  * Jarlebring, Koskela, Mele, Disguised and new Quasi-Newton methods for nonlinear eigenvalue problems, Numer. Algorithms, 79:311-335, 2018. [preprint](https://arxiv.org/abs/1702.08492)
