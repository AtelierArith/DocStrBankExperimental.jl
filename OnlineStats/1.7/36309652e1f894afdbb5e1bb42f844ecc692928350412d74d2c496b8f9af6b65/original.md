```
P2Quantile(τ = 0.5)
```

Calculate the approximate quantile via the P^2 algorithm.  It is more computationally expensive than the algorithms used by [`Quantile`](@ref), but also more exact.

Ref: [https://www.cse.wustl.edu/~jain/papers/ftp/psqr.pdf](https://www.cse.wustl.edu/~jain/papers/ftp/psqr.pdf)

# Example

```
fit!(P2Quantile(.5), rand(10^5))
```
