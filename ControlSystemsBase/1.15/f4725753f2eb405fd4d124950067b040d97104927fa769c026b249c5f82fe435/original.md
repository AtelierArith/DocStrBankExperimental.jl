```
sysr, G, T = baltrunc(sys::StateSpace; atol = √ϵ, rtol=1e-3, n = nothing, residual = false)
```

Reduces the state dimension by calculating a balanced realization of the system sys, such that the observability and reachability gramians of the balanced system are equal and diagonal `diagm(G)`, and truncating it to order `n`. If `n` is not provided, it's chosen such that all states corresponding to singular values less than `atol` and less that `rtol σmax` are removed.

`T` is the projection matrix between the old state `x` and the newstate `z` such that `z = Tx`. `T` will in general be a non-square matrix.

If `residual = true`, matched static gain is achieved through "residualization", i.e., setting

$$
0 = A_{21}x_{1} + A_{22}x_{2} + B_{2}u
$$

where indices 1/2 correspond to the remaining/truncated states respectively.

See also `gram`, `balreal`

Glad, Ljung, Reglerteori: Flervariabla och Olinjära metoder.

For more advanced model reduction, see [RobustAndOptimalControl.jl - Model Reduction](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Model-reduction).

# Extended help

Note: Gramian computations are sensitive to input-output scaling. For the result of a numerical balancing, gramian computation or truncation of MIMO systems to be meaningful, the inputs and outputs of the system must thus be scaled in a meaningful way. A common (but not the only) approach is:

  * The outputs are scaled such that the maximum allowed control error, the maximum expected reference variation, or the maximum expected variation, is unity.
  * The input variables are scaled to have magnitude one. This is done by dividing each variable by its maximum expected or allowed change, i.e., $u_{scaled} = u / u_{max}$

Without such scaling, the result of balancing will depend on the units used to measure the input and output signals, e.g., a change of unit for one output from meter to millimeter will make this output 1000x more important.
