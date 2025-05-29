```
AmplitudeLikelihood(μ, Σ::Union{AbstractVector, AbstractMatrix})
```

Forms the likelihood for amplitudes from the mean vector `μ` and the covariance matrix `Σ`. If Σ is vector or a diagonal matrix then we assume that the argument is the diagonal covariance matrix. If Σ is a full matrix then we assume that a dense covariance was passed

!!! warning
    We do no processing to the data, i.e. the mean μ is not-debiased anywhere. This likelihood will be significantly biased from the true Rice distribution for data points with SNR = μ/Σ < 2. For low SNR data use `RiceAmplitudeLikelihood`

