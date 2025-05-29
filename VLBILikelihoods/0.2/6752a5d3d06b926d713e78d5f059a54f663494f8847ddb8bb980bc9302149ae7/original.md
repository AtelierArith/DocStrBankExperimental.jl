```
RiceAmplitudeLikelihood(μ, Σ::Union{AbstractVector, Diagonal})
```

Forms the likelihood for amplitudes from the mean vector `μ` and the diagonal covariance matrix `Σ`. `Σ` can either be a Diagonal matrix or a vector whose entries are the variance for each data point.

!!! note
    This is the correct likelihood distribution for visibility amplitudes, but it is slower than the Gaussian approximation `AmplitudeLikelihood`. However for low SNR data it is required to get unbiased results.

