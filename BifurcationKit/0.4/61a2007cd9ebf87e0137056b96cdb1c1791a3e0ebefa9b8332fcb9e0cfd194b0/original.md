```julia
struct AutoSwitch{Talg, T} <: BifurcationKit.AbstractContinuationAlgorithm
```

Continuation algorithm which switches automatically between Natural continuation and PALC depending on the stiffness of the branch being continued.

  * `alg::Any`: Continuation algorithm to switch to when Natural is discarded. Typically `PALC()`
  * `tol_param::Any`: tolerance for switching to PALC(), default value = 0.5
