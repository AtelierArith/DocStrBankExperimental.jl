```julia
NILSAS{CS, AD, FDT, RNG, SENSE, gType} <: AbstractShadowingSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of the adjoint-mode, continuous [non-intrusive adjoint least squares shadowing](https://arxiv.org/abs/1801.08674) method. `NILSAS` allows for computing sensitivities of long-time averaged quantities with respect to the parameters of an `ODEProblem` by constraining the computation to the unstable subspace. `NILSAS` employs SciMLSensitivity.jl's continuous adjoint sensitivity methods on each segment to compute (homogeneous and inhomogeneous) adjoint solutions. To avoid an exponential blow-up of the adjoint solutions, the trajectory should be divided into sufficiently small segments, where the adjoint solutions are rescaled on the interfaces. The computational and memory cost of NILSAS scale with the number of unstable, adjoint Lyapunov exponents (instead of the number of states as in the LSS method). `NILSAS` avoids the explicit construction of the Jacobian at each time step, and thus should generally be preferred (for large system sizes) over `AdjointLSS`. `NILSAS` is favorable over `NILSS` for many parameters because NILSAS computes the gradient with respect to multiple parameters with negligible additional cost.

## Constructor

```julia
NILSAS(nseg, nstep, M = nothing; rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    adjoint_sensealg = BacksolveAdjoint(autojacvec = ReverseDiffVJP()),
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    g = nothing)
```

## Arguments

  * `nseg`: Number of segments on full time interval on the attractor.
  * `nstep`: number of steps on each segment.
  * `M`: number of homogeneous adjoint solutions. This number must be bigger or equal than the number of (positive, adjoint) Lyapunov exponents. Default is `nothing`.

## Keyword Arguments

  * `rng`: (Pseudo) random number generator. Used for initializing the terminate conditions of the homogeneous adjoint states (`w`). Default is `Xorshifts.Xoroshiro128Plus(rand(UInt64))`.
  * `adjoint_sensealg`: Continuous adjoint sensitivity method to compute homogeneous and inhomogeneous adjoint solutions on each segment. Default is `BacksolveAdjoint(autojacvec=ReverseDiffVJP())`.

      * `autojacvec`: Calculate the vector-Jacobian product (`J'*v`) via automatic differentiation with special seeding. The default is `true`. The total set of choices are:

          * `false`: the Jacobian is constructed via FiniteDiff.jl
          * `true`: the Jacobian is constructed via ForwardDiff.jl
          * `TrackerVJP`: Uses Tracker.jl for the vjp.
          * `ZygoteVJP`: Uses Zygote.jl for the vjp.
          * `EnzymeVJP`: Uses Enzyme.jl for the vjp.
          * `ReverseDiffVJP(compile=false)`: Uses ReverseDiff.jl for the vjp. `compile` is a boolean for whether to precompile the tape, which should only be done if there are no branches (`if` or `while` statements) in the `f` function.
  * `autodiff`: Use automatic differentiation for constructing the Jacobian if the Jacobian needs to be constructed.  Defaults to `true`.
  * `chunk_size`: Chunk size for forward-mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.
  * `g`: instantaneous objective function of the long-time averaged objective.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s. This `sensealg` does not support events (callbacks). This `sensealg` assumes that the objective is a long-time averaged quantity and ergodic, i.e. the time evolution of the system behaves qualitatively the same over infinite time independent of the specified initial conditions, such that only the sensitivity with respect to the parameters is of interest.

## References

Ni, A., and Talnikar, C., Adjoint sensitivity analysis on chaotic dynamical systems by Non-Intrusive Least Squares Adjoint Shadowing (NILSAS). Journal of Computational Physics 395, 690-709 (2019).
