```
norm_weights(p)
```

This function normalizes a vector of values on the log scale.

$$
π_i=exp(x_i− logsumexp(x)) where logsumexp(x)=b+log∑_{j=1}^n exp(x_j−b)
π_i in [0,1]
$$
