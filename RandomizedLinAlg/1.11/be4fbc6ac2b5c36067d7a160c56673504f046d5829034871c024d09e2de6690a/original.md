```
rnorms(A, iters=1)
```

Estimate matrix norm randomly using `A'A`.

Compute a probabilistic upper bound on the norm of a matrix `A`.

```
ρ = √(‖(A'A)ʲω‖/‖(A'A)ʲ⁻¹ω‖)
```

which is an estimate of the spectral norm of `A` produced by `iters` steps of the power method starting with normalized `ω`, is a lower bound on the true norm by a factor

```
ρ ≤ α ‖A‖
```

with probability greater than `1 - p`, where `p = 4\sqrt(n/(iters-1)) α^(-2iters)`.

# Arguments

  * `A`: matrix whose norm to estimate.
  * `iters::Int = 1`: mumber of power iterations to perform.

## Keywords

  * `p::Real = 0.05`: probability of upper bound failing.
  * `At = A'`: Transpose of `A`.

# Output

Estimate of ‖A‖.

See also [`rnorm`](@ref) for a different estimator that does not require premultiplying by `A'`

# References

Appendix of [^Liberty2007].
