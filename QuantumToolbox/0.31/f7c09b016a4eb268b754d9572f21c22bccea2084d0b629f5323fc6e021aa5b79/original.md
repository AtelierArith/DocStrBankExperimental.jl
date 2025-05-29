```
fcreate(N::Union{Int,Val}, j::Int)
```

Construct a fermionic creation operator acting on the `j`-th site, where the fock space has totally `N`-sites:

Here, we use the [Jordan-Wigner transformation](https://en.wikipedia.org/wiki/Jordan%E2%80%93Wigner_transformation), namely

$$
\hat{d}^\dagger_j = \hat{\sigma}_z^{\otimes j-1} \otimes \hat{\sigma}_{-} \otimes \hat{\mathbb{1}}^{\otimes N-j}
$$

The site index `j` should satisfy: `1 ≤ j ≤ N`.

Note that we put $\hat{\sigma}_{-} = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}$ here because we consider $|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ to be ground (vacant) state, and $|1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$ to be excited (occupied) state.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `fcreate(Val(N), j)` instead of `fcreate(N, j)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

