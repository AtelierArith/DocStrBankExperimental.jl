```
tunneling(N::Int, m::Int=1; sparse::Union{Bool,Val{<:Bool}}=Val(false))
```

Generate a tunneling operator defined as:

$$
\sum_{n=0}^{N-m} | n \rangle\langle n+m | + | n+m \rangle\langle n |,
$$

where $N$ is the number of basis states in the Hilbert space, and $m$ is the number of excitations in tunneling event.

If `sparse=true`, the operator is returned as a sparse matrix, otherwise a dense matrix is returned.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `tunneling(N, m, Val(sparse))` instead of `tunneling(N, m, sparse)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

