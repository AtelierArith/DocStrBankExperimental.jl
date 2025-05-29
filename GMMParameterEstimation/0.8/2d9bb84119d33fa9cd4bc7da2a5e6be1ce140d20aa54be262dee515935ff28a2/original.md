```
sampleMoments(sample::Matrix{Float64}, k; diagonal = false, method = "low")
```

Use the sample to compute the moments necessary for parameter estimation using method of moments with general covariance matrices and mixing coefficients.

Returns moments 0 to 3k for the first dimension, moments 1 through 2k+1 for the other dimensions as a matrix, and a dictionary with indices and moments for the off-diagonal system if `diagonal` is false.
