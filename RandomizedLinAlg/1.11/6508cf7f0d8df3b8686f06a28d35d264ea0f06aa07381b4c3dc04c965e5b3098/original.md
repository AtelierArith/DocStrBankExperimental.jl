```
reigmin(A, iters=1)
```

Estimate minimal eigenvalue randomly.

# Arguments

  * `A`: Matrix whose maximal eigenvalue to estimate.

Must be square and support premultiply (`A*⋅`).

  * `iters::Int=1`: Number of power iterations to run. (Recommended: `iters` ≤ 3)

## Keywords

  * `p::Real=0.05`: Probability that estimate fails to hold as an upper bound.

# Output

Interval `(x, y)` which contains the maximal eigenvalue of `A` with probability `1 - p`.

# References

Corollary of Theorem 1 in [^Dixon1983]
