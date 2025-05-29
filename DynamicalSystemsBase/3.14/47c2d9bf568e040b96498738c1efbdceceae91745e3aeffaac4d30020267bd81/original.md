```
PoincareMap <: DiscreteTimeDynamicalSystem
PoincareMap(ds::CoupledODEs, plane; kwargs...) → pmap
```

A discrete time dynamical system that produces iterations over the Poincaré map[^DatserisParlitz2022] of the given continuous time `ds`. This map is defined as the sequence of points on the Poincaré surface of section, which is defined by the `plane` argument.

Iterating `pmap` also mutates `ds` which is referrenced in `pmap`.

See also [`StroboscopicMap`](@ref), [`poincaresos`](@ref).

## Keyword arguments

  * `direction = -1`: Only crossings with `sign(direction)` are considered to belong to the surface of section. Negative direction means going from less than $b$ to greater than $b$.
  * `u0 = nothing`: Specify an initial state. If `nothing` it is the `current_state(ds)`.
  * `rootkw = (xrtol = 1e-6, atol = 1e-8)`: A `NamedTuple` of keyword arguments passed to `find_zero` from [Roots.jl](https://github.com/JuliaMath/Roots.jl).
  * `Tmax = 1e3`: The argument `Tmax` exists so that the integrator can terminate instead of being evolved for infinite time, to avoid cases where iteration would continue forever for ill-defined hyperplanes or for convergence to fixed points, where the trajectory would never cross again the hyperplane. If during one `step!` the system has been evolved for more than `Tmax`, then `step!(pmap)` will terminate and error.

## Description

The Poincaré surface of section is defined as sequential transversal crossings a trajectory has with any arbitrary manifold, but here the manifold must be a hyperplane. `PoincareMap` iterates over the crossings of the section.

If the state of `ds` is $\mathbf{u} = (u_1, \ldots, u_D)$ then the equation defining a hyperplane is

$$
a_1u_1 + \dots + a_Du_D = \mathbf{a}\cdot\mathbf{u}=b
$$

where $\mathbf{a}, b$ are the parameters of the hyperplane.

In code, `plane` can be either:

  * A `Tuple{Int, <: Real}`, like `(j, r)`: the plane is defined as when the `j`th variable of the system equals the value `r`.
  * A vector of length `D+1`. The first `D` elements of the vector correspond to $\mathbf{a}$ while the last element is $b$.

`PoincareMap` uses `ds`, higher order interpolation from DifferentialEquations.jl, and root finding from Roots.jl, to create a high accuracy estimate of the section.

`PoincareMap` follows the [`DynamicalSystem`](@ref) interface with the following adjustments:

1. `dimension(pmap) == dimension(ds)`, even though the Poincaré map is effectively 1 dimension less.
2. Like [`StroboscopicMap`](@ref) time is discrete and counts the iterations on the surface of section. [`initial_time`](@ref) is always `0` and [`current_time`](@ref) is current iteration number.
3. A new function [`current_crossing_time`](@ref) returns the real time corresponding to the latest crossing of the hyperplane. The corresponding state on the hyperplane is `current_state(pmap)` as expected.
4. For the special case of `plane` being a `Tuple{Int, <:Real}`, a special `reinit!` method is allowed with input state of length `D-1` instead of `D`, i.e., a reduced state already on the hyperplane that is then converted into the `D` dimensional state.
5. The `initial_state(pmap)` returns the state initial state of the map. This is not `u0` because `u0` is evolved forwards until it resides on the Poincaré plane.
6. In the `reinit!` function, the `t0` keyword denotes the starting time of the continuous time dynamical system, as the starting time of the `PoincareMap` is by definition always 0.

## Example

```julia
using DynamicalSystemsBase, PredefinedDynamicalSystems
ds = Systems.rikitake(zeros(3); μ = 0.47, α = 1.0)
pmap = poincaremap(ds, (3, 0.0))
step!(pmap)
next_state_on_psos = current_state(pmap)
```

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
