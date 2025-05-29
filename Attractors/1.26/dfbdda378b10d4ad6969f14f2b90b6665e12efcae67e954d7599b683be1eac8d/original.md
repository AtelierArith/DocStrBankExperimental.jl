```
stagger_and_step(ds::DynamicalSystem, x0, N::Int, 
    isinside::Function; kwargs...) -> trajectory
```

Implement the stagger-and-step method  [Sweet2001](@cite) and [Sala2016](@cite) to approximate the invariant  non-attracting set governing the chaotic transient dynamics  of a system, namely the stable manifold of a chaotic saddle. 

Given the dynamical system `ds` and a initial guess `x0` in a  region *with no attractors* defined by the membership function  `isinside`, the algorithm returns a `StateSpaceState` named `trajectory`  of `N` points from the phase space close to the stable manifold.  If we set one of this point as an initial condition of `ds`,  the trajectory escape from the region after at least `Tm`  steps of `ds`. The search is stochastic and depends on the  parameter `δ` defining a (small) neighborhood of search. 

The function `isinside(x)` must return `true` if the point `x` is  inside the chosen bounded region and `false` otherwise. See  [`statespace_sampler`](@ref) as a helper to construct this  function.

## Keyword arguments

  * `δ = 1e-10`: A small number constraining the random search around a particular point. The interpretation of this  number will depend on the probability distribution chosen  for the sampling (see `stagger_mode`).
  * `Tm = 30`: The minimum number of steps of `ds` before  the trajectory escapes from the bounding box defined by `isinside`.
  * `max_steps = 10^5`: The search for a new candidate point may  fail at some point. If the search fails after `max_steps`,  a new initial point is set and the method starts from a new point.
  * `max_escape_time = 10000`: If the trajectory stays in the  defined region after `max_escape_time` steps, there is probably an attractor in the region and the algorithm will throw an error.
  * `stagger_mode = :exp`: There are several ways to produce  candidate points `x` to fulfill the condition `T(x) > Tm`.  The available methods are: 

      * `:exp`: A candidate is sampled from a truncated exponential  distribution in a random direction `u` around the current `x` such that `x_c = x + u*r`. `r = 10^-s` with `s` taken from a uniform distribution in [-15, δ].
      * `:unif`: The next candidate is `x_c = x + u*r` with `r`  taken from a uniform distribution [0,δ] and `u` a random  direction around `x`.
      * `:adaptive`: The next candidate is `x_c = x + u*r` with  `r` drawn from a gaussian distribution with variance  δ  and mean zero. The variance is adapted according to a free parameter `γ` such that: `δ = δ/γ` if no candidate is found and `δ = δ*γ` when it succeeds.
  * `γ = 1.1`: It is free parameter for the adaptive stagger method `:adaptive`.
  * `δ₀ = 1.0`: This is the radius for the first stagger  trajectory search. The algorithm looks for a point  sufficiently close to the saddle before switching to the  stagger-and-step routine. The search radius must be large  enough to find a suitable initial candidate.  To type `δ₀` use `\delta<TAB>\_0<TAB>`.
  * `rng::AbstractRNG = Xoshiro()`:  Random number generator. Use this for reproducibility.

## Description

The method relies on the stagger-and-step algorithm that  searches initial conditions close to the saddle with escapes time  `T(x_n) > Tm`. The function `T` represents the time at which the trajectory with initial condition `x_n` steps out  from a region defined by the user (see the argument `isinside`). This time is a discrete or continuous variable depending on  the dynamical system `ds`.

Given the dynamical mapping `F`, if the step `x_{n+1} =  F(x_n)` fulfills the condition `T(x_{n+1}) > Tm` we accept  this next point, this is the *step* part of the method. If  not, the method search randomly the next point in a  neighborhood following a given probability distribution, this  is the *stagger* part. The *stagger* process sometimes fails to find  a new candidate and a new starting point of the trajectory is chosen  within the defined region. See the keyword argument  `stagger_mode` for the different available methods.   

The method produces a pseudo-trajectory of `N` points δ-close to the stable manifold of the chaotic saddle. 
