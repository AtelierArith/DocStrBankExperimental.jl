```
biascorrect(r::VectorAutoregression; kwargs...)
```

Correct the bias of the least-squares coefficient estimates in `r` with Pope's formula. The corrected estimates can be retrieved from the returned object with [`coefcorrected`](@ref).

# Reference

**Pope, Alun L.** 1990. "Biases of Estimators in Multivariate Non-Gaussian Autoregressions." *Journal of Time Series Analysis* 11 (3): 249–258.
