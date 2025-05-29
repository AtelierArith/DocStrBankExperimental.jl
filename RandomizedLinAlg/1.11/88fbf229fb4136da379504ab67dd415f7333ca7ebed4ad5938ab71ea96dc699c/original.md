```
rcond(A, iters=1)
```

Estimate matrix condition number randomly.

# Arguments

  * `A`: matrix whose condition number to estimate. Must be square and

support premultiply (`A*⋅`) and solve (`A\⋅`).

  * `iters::Int = 1`: number of power iterations to run.

## Keywords

  * `p::Real = 0.05`: probability that estimate fails to hold as an upper bound.

# Output

Interval `(x, y)` which contains `κ(A)` with probability `1 - p`.

# Implementation note

[^Dixon1983] originally describes this as a computation that can be done by computing the necessary number of power iterations given p and the desired accuracy parameter `θ=y/x`. However, these bounds were only derived under the assumptions of exact arithmetic. Empirically, `iters≥4` has been seen to result in incorrect results in that the computed interval does not contain the true condition number. This implemention therefore makes `iters` an explicitly user-controllable parameter from which to infer the accuracy parameter and hence the interval containing `κ(A)`. ```
