```
randrange(X,Y,n; <keyword arguments>)
```

Structure exploiting randomized range approximation of n-mode matricization of Hadamard product (X ∗ Y)ₙ, where X and Y are ttensors.

### Arguments:

  * `reqrank::Integer`: Requested rank. Optional.
  * `tol::Number/Vector`: Tolerance. Default: 1e-8.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `r`: Number of samples for stopping criterion. Default: r=10.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
