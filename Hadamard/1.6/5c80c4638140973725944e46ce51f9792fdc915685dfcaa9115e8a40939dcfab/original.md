```
fwht_dyadic(X, dims=1:ndims(X))
```

Return the fast Walsh-Hadamard transform (WHT) of the array `X` along the dimensions `dims` (an integer, tuple, or array of dimensions, defaulting to all dimensions). Only power-of-two sizes (along the transformed dimensions) are supported.  The result is returned in the dyadic (Paley, bit-reversed) ordering.

Our WHT is normalized so that the forward transform has a `1/n` coefficient (where `n` is the product of the transformed dimensions) and the inverse WHT has no scaling factor.
