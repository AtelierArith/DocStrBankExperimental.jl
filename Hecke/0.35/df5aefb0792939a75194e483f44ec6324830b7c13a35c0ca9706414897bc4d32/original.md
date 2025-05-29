```
enumerate_quadratic_triples(
    Q::MatrixElem{T},
    b::MatrixElem{T},
    c::RationalUnion;
    algorithm::Symbol=:short_vectors,
    equal::Bool=false
  ) where T <: Union{ZZRingElem, QQFieldElem}
                          -> Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}
```

Given the Gram matrix $Q$ of a positive definite quadratic form, return the list of pairs $(v, d)$ so that $v$ satisfies $v*Q*v^T + 2*v*Q*b^T + c \leq 0$ where $b$ is seen as a row vector and $c$ is a rational number. Moreover $d$ is so that $(v-b)*Q*(v-b)^T = d$.

For the moment, only the algorithm `:short_vectors` is available. The function uses the data required for the closest vector problem for the quadratic triple `[Q, b, c]`; in particular, $d$ is smaller than the associated upper-bound $M$ (see [`close_vectors`](@ref)).

If `equal` is set to `true`, the function returns only the pairs $(v, d)$ such that $d=M$.
