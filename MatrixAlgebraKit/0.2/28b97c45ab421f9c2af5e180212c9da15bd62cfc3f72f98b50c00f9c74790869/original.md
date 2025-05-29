```
LAPACK_HouseholderQR(; blocksize, positive = false, pivoted = false)
```

Algorithm type to denote the standard LAPACK algorithm for computing the QR decomposition of a matrix using Householder reflectors. The specific LAPACK function can be controlled using the keyword arugments, i.e.  `?geqrt` will be chosen if `blocksize > 1`. With `blocksize == 1`, `?geqrf` will be chosen if `pivoted == false` and `?geqp3` will be chosen if `pivoted == true`. The keyword `positive=true` can be used to ensure that the diagonal elements of `R` are non-negative.
