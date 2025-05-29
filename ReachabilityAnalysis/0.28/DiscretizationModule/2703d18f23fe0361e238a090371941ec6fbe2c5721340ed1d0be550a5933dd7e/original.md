```
discretize(ivp::IVP, δ, alg::AbstractApproximationModel)
```

Set-based conservative discretization of a continuous-time initial value problem into a discrete-time problem.

### Input

  * `ivp`   – initial value problem for a linear ODE in canonical form (see `Notes` below)
  * `δ`     – step size
  * `alg`   – algorithm used to compute the approximation model

### Output

The initial value problem of a discrete system.

### Notes

Different approximation algorithms and their respective options are described in the docstring of each method. Here is a list of all the available approximation models:

```jldoctest
julia> subtypes(ReachabilityAnalysis.DiscretizationModule.AbstractApproximationModel)
9-element Vector{Any}:
 Backward
 CorrectionHull
 FirstOrder
 FirstOrderZonotope
 Forward
 ForwardBackward
 NoBloating
 SecondOrderddt
 StepIntersect
```

Initial-value problems considered in this function are of the form

$$
x' = Ax(t) + u(t),\qquad x(0) ∈ \mathcal{X}_0,\qquad (1)
$$

and where $u(t) ∈ U(k)$ add where $\{U(k)\}_k$ is a sequence of sets of non-deterministic inputs and $\mathcal{X}_0$ is the set of initial states. Other problems, e.g. $x' = Ax(t) + Bu(t)$ can be brought to the canonical form with the function [`normalize`](@ref).

For references to the original papers introducing each algorithm, see the docstrings, e.g. `?Forward`.
