```
gelmandiag(samples::AbstractArray{<:Real,3}; alpha::Real=0.95)
```

Compute the Gelman, Rubin and Brooks diagnostics [^Gelman1992] [^Brooks1998] on `samples` with shape `(draws, chains, parameters)`.  Values of the diagnostic’s potential scale reduction factor (PSRF) that are close to one suggest convergence.  As a rule-of-thumb, convergence is rejected if the 97.5 percentile of a PSRF is greater than 1.2.

[^Gelman1992]: Gelman, A., & Rubin, D. B. (1992). Inference from iterative simulation using multiple sequences. Statistical science, 7(4), 457-472.

[^Brooks1998]: Brooks, S. P., & Gelman, A. (1998). General methods for monitoring convergence of iterative simulations. Journal of computational and graphical statistics, 7(4), 434-455.
