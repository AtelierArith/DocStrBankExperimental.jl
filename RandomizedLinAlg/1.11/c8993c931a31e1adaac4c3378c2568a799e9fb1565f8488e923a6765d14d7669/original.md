```
rnorm(A, mvps)
```

Compute a probabilistic upper bound on the norm of a matrix `A`. `‖A‖ ≤ α √(2/π) maxᵢ ‖Aωᵢ‖` with probability `p=α^(-mvps)`.

# Arguments

  * `A`: matrix whose norm to estimate.
  * `mvps::Int`: number of matrix-vector products to compute.

## Keywords

  * `p::Real=0.05`: probability of upper bound failing.

# Output

Estimate of ‖A‖.

See also [`rnorms`](@ref) for a different estimator that uses  premultiplying by both `A` and `A'`.

# References

Lemma 4.1 of Halko2011
