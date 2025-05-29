```
BFGSCache(B)
```

Make the cache for the BFGS optimizer based on the array `B`.

It stores an array for the gradient of the previous time step `B` and the inverse of the Hessian matrix `H`.

The cache for the inverse of the Hessian is initialized with the idendity. The cache for the previous gradient information is initialized with the zero vector.

Note that the cache for `H` is changed iteratively, whereas the cache for `B` is newly assigned at every time step.
