Return the recurrence coefficients `α_n` and `β_n` for the monic orthogonal polynomials (i.e., with leading order coefficient `1`). The recurrence relation is

```
p_{n+1}(x) = (x-α_n)p_n(x) - β_n p_{n-1}(x).
```

The result is a vector with indices starting at `1` (such that `α_n` above is given by `α[n+1]`). The last value is `α_{n-1} = α[n]`.
