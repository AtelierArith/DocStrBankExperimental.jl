```
smssvd(X, d, stdThresholds=10 .^ range(-2,stop=0,length=100); nbrIter=10, maxSignalDim=typemax(Int)) -> (U,Σ,V,ps,signalDimensions,selectedVariables)
```

Computes the SubMatrix Selection Singular Value Decomposition (SMSSVD) of a matrix X.

**Inputs**

  * `X`: PxN data matrix (P variables and N samples).
  * `d`: Number of dimension in the result.
  * `stdThresholds`: Standard deviation filtering thresholds at which the Projection Score will be evaluated. Expressed as fractions of the maximum standard deviation of a variable in X. Should be a vector of increasing values between 0 and 1.

**Outputs**

  * `U`: Pxd matrix of left singular vectors (variable representation).
  * `S`: d-vector of singular values.
  * `V`: Nxd matrix of right singular vectors (sample representation).
  * `ps`: d x length(stdThresholds) matrix with all Projection Scores. Useful for plotting.
  * `signalDimensions`: Vector with the number of dimensions in each signal detected by SMSSVD.
  * `selectedVariables`: For each signal, a bitmask showing the variables selected by Projection Score.
