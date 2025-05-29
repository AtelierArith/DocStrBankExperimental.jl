```
struct NILSS{CS,AD,FDT,RNG,nType,gType} <: AbstractShadowingSensitivityAlgorithm{CS,AD,FDT}
```

An implementation of the forward-mode, continuous [non-intrusive least squares shadowing](https://arxiv.org/abs/1611.00880) method. `NILSS` allows for computing sensitivities of long-time averaged quantities with respect to the parameters of an `ODEProblem` by constraining the computation to the unstable subspace. `NILSS` employs the continuous-time `ForwardSensitivity` method as tangent solver. To avoid an exponential blow-up of the (homogeneous and inhomogeneous) tangent solutions, the trajectory should be divided into sufficiently small segments, where the tangent solutions are rescaled on the interfaces. The computational and memory cost of NILSS scale with the number of unstable (positive) Lyapunov exponents (instead of the number of states, as in the LSS method). `NILSS` avoids the explicit construction of the Jacobian at each time step, and thus should generally be preferred (for large system sizes) over `ForwardLSS`.

## Constructor

```julia
NILSS(nseg, nstep; nus = nothing,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff,
    g = nothing)
```

## Arguments

  * `nseg`: Number of segments on full time interval on the attractor.
  * `nstep`: number of steps on each segment.

## Keyword Arguments

  * `nus`: Dimension of the unstable subspace. Default is `nothing`. `nus` must be smaller or equal to the state dimension (`length(u0)`). With the default choice, `nus = length(u0) - 1` will be set at compile time.
  * `rng`: (Pseudo) random number generator. Used for initializing the homogeneous tangent states (`w`). Default is `Xorshifts.Xoroshiro128Plus(rand(UInt64))`.
  * `autodiff`: Use automatic differentiation in the internal sensitivity algorithm computations. Default is `true`.
  * `chunk_size`: Chunk size for forward mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `autojacvec`: Calculate the Jacobian-vector product via automatic differentiation with special seeding.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.
  * `g`: instantaneous objective function of the long-time averaged objective.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s. This `sensealg` does not support events (callbacks). This `sensealg` assumes that the objective is a long-time averaged quantity and ergodic, i.e. the time evolution of the system behaves qualitatively the same over infinite time independent of the specified initial conditions, such that only the sensitivity with respect to the parameters is of interest.

## References

Ni, A., Blonigan, P. J., Chater, M., Wang, Q., Zhang, Z., Sensitivity analy- sis on chaotic dynamical system by Non-Intrusive Least Square Shadowing (NI-LSS), in: 46th AIAA Fluid Dynamics Conference, AIAA AVIATION Forum (AIAA 2016-4399), American Institute of Aeronautics and Astronautics, 1–16 (2016).

Ni, A., and Wang, Q. Sensitivity analysis on chaotic dynamical systems by Non-Intrusive Least Squares Shadowing (NILSS). Journal of Computational Physics 347, 56-77 (2017).
