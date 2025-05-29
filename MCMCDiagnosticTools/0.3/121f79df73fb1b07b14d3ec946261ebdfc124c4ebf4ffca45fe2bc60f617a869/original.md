```
gelmandiag_multivariate(samples::AbstractArray{<:Real,3}; alpha::Real=0.05)
```

Compute the multivariate Gelman, Rubin and Brooks diagnostics on `samples` with shape `(draws, chains, parameters)`.
