```
(graph,cref)=graph_bbcs_cheb_exp(k;T=Complex{BigFloat})
```

Computes a polynomial evaluation approximating the exponential for skew-Hermitian matrices using `k` matrix multiplications following the procedure in the reference.

For `k > 5` it resorts to scaling-and-squaring of the `k = 5` graph. The graph is in the degopt format, see [`graph_degopt`](@ref).

**Reference**

1. P. Bader, S. Blanes, F. Casas, M. Seydaoglu. "An efficient algorithm to compute the exponential of skew-Hermitian matrices for the time integration of the Schrödinger equation". [arXiv:2103.10132 [math.NA]](https://arxiv.org/abs/2103.10132), 2021.
