```
counts_and_outcomes(o::OutcomeSpace, x) → (cts::Counts, Ω)
```

Discretize/encode `x` (which must be sortable) into a finite set of outcomes `Ω` specified by the provided [`OutcomeSpace`](@ref) `o`, and then count how often each outcome `Ωᵢ ∈ Ω` (i.e. each "discretized value", or "encoded symbol") appears.

Return a tuple where the first element is a [`Counts`](@ref) instance, which is vector-like and contains the counts, and where the second element `Ω` are the outcomes corresponding to the counts, such that `cts[i]` is the count for the outcome `Ω[i]`.

The outcomes are actually included in `cts`, and you can use the [`outcomes`](@ref) function on the `cts` to get them. `counts_and_outcomes` returns both for backwards compatibility.

```
counts_and_outcomes(x) → cts::Counts
```

If no [`OutcomeSpace`](@ref) is specified, then [`UniqueElements`](@ref) is used as the outcome space.

## Description

For [`OutcomeSpace`](@ref)s that uses [`encode`](@ref) to discretize, it is possible to count how often each outcome $\omega_i \in \Omega$, where $\Omega$ is the set of possible outcomes, is observed in the discretized/encoded input data. Thus, we can assign to each outcome $\omega_i$ a count $f(\omega_i)$, such that $\sum_{i=1}^N f(\omega_i) = N$, where $N$ is the number of observations in the (encoded) input data. `counts` returns the counts $f(\omega_i)_{obs}$ and outcomes only for the *observed* outcomes $\omega_i^{obs}$ (those outcomes that actually appear in the input data). If you need the counts for *unobserved* outcomes as well, use [`allcounts_and_outcomes`](@ref).
