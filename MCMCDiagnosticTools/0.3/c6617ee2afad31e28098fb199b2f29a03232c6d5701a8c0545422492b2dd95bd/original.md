```
discretediag(samples::AbstractArray{<:Real,3}; frac=0.3, method=:weiss, nsim=1_000)
```

Compute discrete diagnostic on `samples` with shape `(draws, chains, parameters)`.

`method` can be one of `:weiss`, `:hangartner`, `:DARBOOT`, `:MCBOOT`, `:billinsgley`, and `:billingsleyBOOT`.

# References

Benjamin E. Deonovic, & Brian J. Smith. (2017). Convergence diagnostics for MCMC draws of a categorical variable.
