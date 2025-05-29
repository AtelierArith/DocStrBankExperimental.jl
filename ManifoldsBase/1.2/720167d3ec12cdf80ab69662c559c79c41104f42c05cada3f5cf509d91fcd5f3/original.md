```
manifold_dimension(M::PowerManifold)
```

Returns the manifold-dimension of an [`PowerManifold`](@ref) `M` $=\mathcal N = (\mathcal M)^{n_1,…,n_d}$, i.e. with $n=(n_1,…,n_d)$ the array size of the power manifold and $d_{\mathcal M}$ the dimension of the base manifold $\mathcal M$, the manifold is of dimension

$$
\dim(\mathcal N) = \dim(\mathcal M)\prod_{i=1}^d n_i = n_1n_2⋅…⋅ n_d \dim(\mathcal M).
$$
