```
clenshaw_curtis(n, [T])
```

Compute `n` weights for the Clenshaw-Curtis rule, corresponding to `n` evenly spaced nodes from 0 to π inclusive.  That is, the nodes are located at

$$
\theta_k = k \frac{\pi}{n-1} \quad k=0, \ldots, n-1.
$$

This function uses [Waldvogel's method](@cite Waldvogel_2006).

The type `T` may be any `AbstractFloat`, but defaults to `Float64`.
