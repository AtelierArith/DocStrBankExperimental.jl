```
inner(M::Hyperrectangle, p, X, Y)
```

Compute the inner product on the [`Hyperrectangle`](@ref) `M`, which is just the inner product on the real-valued vector space of arrays (or tensors) of size $n_1 × n_2  ×  …  × n_i$, i.e.

$$
g_p(X,Y) = \sum_{k ∈ I} X_{k} Y_{k},
$$

where $I$ is the set of vectors $k ∈ ℕ^i$, such that for all

$i ≤ j ≤ i$ it holds $1 ≤ k_j ≤ n_j$.

For the special case of $i ≤ 2$, i.e. matrices and vectors, this simplifies to

$$
g_p(X,Y) = \operatorname{tr}(X^{\mathrm{T}}Y),
$$

where $⋅^{\mathrm{T}}$ denotes transposition.
