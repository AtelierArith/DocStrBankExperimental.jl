```
SDPBarrierOptions(; kwargs...)
```

The keyword arguments which can be specified are:

  * `c_init`: (default 1.0) initial value for the coefficient `c` that is multiplied by the barrier term, could be a real number or vector in the case of multiple semidefinite constraints.
  * `c_decr`: (default 0.1) decreasing rate (< 1) that multiplies the barrier term in every iteration, could be either a real number or a vector in the case of multiple semidefinite constraints.
  * `n_iter`: (default 20) number of sub-problems to solve in the barrier method.
  * `sub_options`: options for the sub-problem's solver
  * `keep_all`: (default `falue`) if set to `true`, `SDPBarrierResult` stores the results from all the iterations
