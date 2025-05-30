```
fejer2(n, [T])
```

Compute `n` weights for Fejér's second rule, corresponding to `n` evenly spaced nodes between 0 and π exclusive.  That is, the nodes are located at

$$
\theta_k = k \frac{\pi}{n+1} \quad k=1, \ldots, n.
$$

This function uses [Waldvogel's method](@cite Waldvogel_2006).  However, contrary to Waldvogel's notation, this routine *does not* include the weight corresponding to the ϑ=0 or π nodes, which both have weight 0.

The type `T` may be any `AbstractFloat`, but defaults to `Float64`.
