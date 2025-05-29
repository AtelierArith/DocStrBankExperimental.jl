```
sigmoidNorm!(K,p;float_type=nothing)
```

This function normalizes a vector of values using a logistic function by precallocating an its output and performs operations in place. Normalization only occurs up until the Kth element in the vector

$$
f(x_i) = frac{1}{1 + e^{-x_i}} text{ for } i in {1,..,K}
$$
