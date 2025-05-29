```
ConfidenceRegions(DM::DataModel, Range::AbstractVector)
```

Computes the boundaries of confidence regions for two-dimensional parameter spaces given a vector or range of confidence levels. A convenient interface which extends this to higher dimensions is currently still under development.

For example,

```julia
ConfidenceRegions(DM, 1:3; tol=1e-9)
```

computes the $1\sigma$, $2\sigma$ and $3\sigma$ confidence regions associated with a given `DataModel` using a solver tolerance of $10^{-9}$.

Keyword arguments:

  * `IsConfVol = true` can be used to specify the desired confidence level directly in terms of a probability $p \in [0,1]$ instead of in units of standard deviations $\sigma$,
  * `tol` can be used to quantify the tolerance with which the ODE which defines the confidence boundary is solved (default `tol = 1e-9`),
  * `meth` can be used to specify the solver algorithm (default `meth = Tsit5()`),
  * `ADmode=Val(false)` computes the Score by separately evaluating the `model` as well as the Jacobian `dmodel` provided in `DM`. Other choices of `ADmode` directly compute the Score by differentiating the formula the log-likelihood, i.e. only one evaluation on a dual variable is performed.
  * `parallel = true` parallelizes the computations of the separate confidence regions provided each process has access to the necessary objects,
  * `dof` can be used to manually specify the degrees of freedom.
