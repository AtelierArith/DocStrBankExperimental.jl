```
norm(sys, p=2; tol=1e-6)
```

`norm(sys)` or `norm(sys,2)` computes the H2 norm of the LTI system `sys`.

`norm(sys, Inf)` computes the H∞ norm of the LTI system `sys`. The H∞ norm is the same as the L∞ for stable systems, and Inf for unstable systems. If the peak gain frequency is required as well, use the function `hinfnorm` instead. See [`hinfnorm`](@ref) for further documentation.

`tol` is an optional keyword argument, used only for the computation of L∞ norms. It represents the desired relative accuracy for the computed L∞ norm (this is not an absolute certificate however).

`sys` is first converted to a `StateSpace` model if needed.
