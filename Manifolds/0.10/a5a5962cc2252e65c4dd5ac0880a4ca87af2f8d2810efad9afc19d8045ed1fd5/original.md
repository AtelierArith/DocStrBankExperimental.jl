```
inner(M::Euclidean, p, X, Y)
```

Compute the inner product on the [`Euclidean`](@ref) `M`, which is just the inner product on the real-valued or complex valued vector space of arrays (or tensors) of size $n_1 × n_2  ×  …  × n_i$, i.e.

$$
g_p(X,Y) = \sum_{k ∈ I} \overline{X}_{k} Y_{k},
$$

where $I$ is the set of vectors $k ∈ ℕ^i$, such that for all

$i ≤ j ≤ i$ it holds $1 ≤ k_j ≤ n_j$ and $\overline{⋅}$ denotes the complex conjugate.

For the special case of $i ≤ 2$, i.e. matrices and vectors, this simplifies to

$$
g_p(X,Y) = \operatorname{tr}(X^{\mathrm{H}}Y),
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
