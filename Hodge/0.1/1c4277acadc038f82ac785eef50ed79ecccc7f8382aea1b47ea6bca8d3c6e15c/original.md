```
Cochain{R, n}
```

Represent the `n`-th group $C^n(K; R)$ of cochains over the ring `R` whose basespace is the simplicial complex $K$.

For constructing Cochains, see also the methods [`zero_cochain`](@ref) and [`indicator_cochain`](@ref).

The elements of this type may be seem as functions from the n-simplices of `K` to `R` or as skew-symmetric n-tensors over the vertices of `K`. This second perspective follows the ideas from the paper:

  * Jiang, X., Lim, L., Yao, Y. et al. Statistical ranking and combinatorial Hodge theory. Math. Program. 127, 203–244 (2011). https://doi.org/10.1007/s10107-010-0419-x
