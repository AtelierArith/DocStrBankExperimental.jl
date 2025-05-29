```
generalPerfectMoments(d, k, w, true_means, true_covariances; method = "low")
```

Use the given parameters to compute the exact moments necessary for parameter estimation with general covariance matrices.

Returns moments 0 to 3k for the first dimension, moments 1 through 2k+1 for the other dimensions as a matrix, and a dictionary with indices and moments for the off-diagonal system.
