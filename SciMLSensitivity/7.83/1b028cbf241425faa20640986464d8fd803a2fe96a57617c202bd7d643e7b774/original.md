```julia
ForwardLSS{CS, AD, FDT, RType, gType} <: AbstractShadowingSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of the discrete, forward-mode [least squares shadowing](https://arxiv.org/abs/1204.0159) (LSS) method. LSS replaces the ill-conditioned initial value problem (`ODEProblem`) for chaotic systems by a well-conditioned least-squares problem. This allows for computing sensitivities of long-time averaged quantities with respect to the parameters of the `ODEProblem`. The computational cost of LSS scales as (number of states x number of time steps). Converges to the correct sensitivity at a rate of `T^(-1/2)`, where `T` is the time of the trajectory. See `NILSS()` and `NILSAS()` for a more efficient non-intrusive formulation.

## Constructor

```julia
ForwardLSS(;
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    LSSregularizer = TimeDilation(10.0, 0.0, 0.0),
    g = nothing)
```

## Keyword Arguments

  * `autodiff`: Use automatic differentiation for constructing the Jacobian if the Jacobian needs to be constructed.  Defaults to `true`.
  * `chunk_size`: Chunk size for forward-mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.
  * `LSSregularizer`: Using `LSSregularizer`, one can choose between three different regularization routines. The default choice is `TimeDilation(10.0,0.0,0.0)`.

      * `CosWindowing()`: cos windowing of the time grid, i.e. the time grid (saved time steps) is transformed using a cosine.
      * `Cos2Windowing()`: cos^2 windowing of the time grid.
      * `TimeDilation(alpha::Number,t0skip::Number,t1skip::Number)`: Corresponds to a time dilation. `alpha` controls the weight. `t0skip` and `t1skip` indicate the times truncated at the beginning and end of the trajectory, respectively.
  * `g`: instantaneous objective function of the long-time averaged objective.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s. This `sensealg` does not support events (callbacks). This `sensealg` assumes that the objective is a long-time averaged quantity and ergodic, i.e. the time evolution of the system behaves qualitatively the same over infinite time independent of the specified initial conditions, such that only the sensitivity with respect to the parameters is of interest.

## References

Wang, Q., Hu, R., and Blonigan, P. Least squares shadowing sensitivity analysis of chaotic limit cycle oscillations. Journal of Computational Physics, 267, 210-224 (2014).

Wang, Q., Convergence of the Least Squares Shadowing Method for Computing Derivative of Ergodic Averages, SIAM Journal on Numerical Analysis, 52, 156–170 (2014).

Blonigan, P., Gomez, S., Wang, Q., Least Squares Shadowing for sensitivity analysis of turbulent fluid flows, in: 52nd Aerospace Sciences Meeting, 1–24 (2014).
