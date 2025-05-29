```
norm_weights3!(K,p;float_type=nothing)
```

This function normalizes a vector of values on the log scale by precallocating an its output and performs operations in place. Normalization only occurs up until the Kth element in the vector

$$
π_i=exp(x_i− logsumexp(x)) text{ where } logsumexp(x)=b+log∑_{j=1}^K exp(x_j−b)
text{ for } π_i in [0,1] text{and} i in {1,..,K}
$$
