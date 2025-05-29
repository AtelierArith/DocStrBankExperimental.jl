```
computeSP2(n::Integer,β::AbstractVector{<:Real})
computeSP2(n::Integer,op::AbstractOrthoPoly) = computeSP2(n,op.β)
computeSP2(op::AbstractOrthoPoly) = computeSP2(op.deg,op.β)
```

Computes the `n` *regular* scalar products aka 2-norms of the orthogonal polynomials, namely

$$
\|ϕ_i\|^2 = \langle \phi_i,\phi_i\rangle \quad \forall i \in \{ 0,\dots,n \}.
$$

Notice that only the values of `β` of the recurrence coefficients `(α,β)` are required. The computation is based on equation (1.3.7) from Gautschi, W. "Orthogonal Polynomials: Computation and Approximation". Whenever there exists an analytical expression for `β`, this function should be used.

The function is multiple-dispatched to facilitate its use with `AbstractOrthoPoly`.
