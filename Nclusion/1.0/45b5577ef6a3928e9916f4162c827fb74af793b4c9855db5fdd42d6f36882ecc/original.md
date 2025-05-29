```
norm_weights3!(p;float_type=nothing)
```

This function normalizes a vector of values on the log scale by precallocating an its output and performs operations in place.

$$
π_i=exp(x_i− logsumexp(x)) where logsumexp(x)=b+log∑_{j=1}^n exp(x_j−b)
π_i in [0,1]
$$
