```
Ninf, ω_peak = linfnorm(sys; tol=1e-6)
```

Compute the L∞ norm `Ninf` of the LTI system `sys`, together with a frequency `ω_peak` at which the gain `Ninf` is achieved.

`Ninf := sup_ω σ_max[sys(iω)]` (σ_max denotes the largest singular value)

`tol` is an optional keyword argument representing the desired relative accuracy for the computed L∞ norm (this is not an absolute certificate however).

`sys` is first converted to a state space model if needed.

The continuous-time L∞ norm computation implements the 'two-step algorithm' in:
**N.A. Bruinsma and M. Steinbuch**, 'A fast algorithm to compute the H∞-norm of a transfer function matrix', Systems and Control Letters (1990), pp. 287-293.

For the discrete-time version, see:
**P. Bongers, O. Bosgra, M. Steinbuch**, 'L∞-norm calculation for generalized state space systems in continuous and discrete time', American Control Conference, 1991.

See also [`hinfnorm`](@ref).
