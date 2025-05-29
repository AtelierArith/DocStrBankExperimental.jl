```
normToProb3!(K,p;float_type=nothing)
```

This function normalizes a vector of values by precallocating an its output and performs operations in place. Normalization only occurs up until the Kth element in the vector

$$
w_i = frac{x_i}{∑_{j=1}^K x_j} text{ for } i in {1,..,K} 
$$
