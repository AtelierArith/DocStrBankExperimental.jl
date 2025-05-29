```
mleKS{T<:AbstractFloat}(data::AbstractVector{T})
```

Return the maximum likelihood estimate and standard error of the exponent of a power law applied to the sorted vector `data`. Also return the Kolmogorov-Smirnov statistic. Results are returned in an instance of type `MLEKS`.
