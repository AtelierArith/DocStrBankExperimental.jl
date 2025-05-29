```
LAPACK_HouseholderLQ(; blocksize, positive = false)
```

Algorithm type to denote the standard LAPACK algorithm for computing the LQ decomposition of a matrix using Householder reflectors. The specific LAPACK function can be controlled using the keyword arugments, i.e. `?gelqt` will be chosen if `blocksize > 1` or `?gelqf` will be chosen if `blocksize == 1`. The keyword `positive=true` can be used to ensure that the diagonal elements of `L` are non-negative.
