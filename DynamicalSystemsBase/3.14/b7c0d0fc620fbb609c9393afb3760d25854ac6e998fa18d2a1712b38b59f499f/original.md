```
ProjectedDynamicalSystem <: DynamicalSystem
ProjectedDynamicalSystem(ds::DynamicalSystem, projection, complete_state)
```

A dynamical system that represents a projection of an existing `ds` on a (projected) space.

The `projection` defines the projected space. If `projection isa AbstractVector{Int}`, then the projected space is simply the variable indices that `projection` contains. Otherwise, `projection` can be an arbitrary function that given the state of the original system `ds`, returns the state in the projected space. In this case the projected space can be equal, or even higher-dimensional, than the original.

`complete_state` produces the state for the original system from the projected state. `complete_state` can always be a function that given the projected state returns a state in the original space. However, if `projection isa AbstractVector{Int}`, then `complete_state` can also be a vector that contains the values of the *remaining* variables of the system, i.e., those *not* contained in the projected space. In this case the projected space needs to be lower-dimensional than the original.

Notice that `ProjectedDynamicalSystem` does not require an invertible projection, `complete_state` is only used during [`reinit!`](@ref). `ProjectedDynamicalSystem` is in fact a rather trivial wrapper of `ds` which steps it as normal in the original state space and only projects as a last step, e.g., during [`current_state`](@ref).

## Examples

Case 1: project 5-dimensional system to its last two dimensions.

```julia
ds = Systems.lorenz96(5)
projection = [4, 5]
complete_state = [0.0, 0.0, 0.0] # completed state just in the plane of last two dimensions
prods = ProjectedDynamicalSystem(ds, projection, complete_state)
reinit!(prods, [0.2, 0.4])
step!(prods)
current_state(prods)
```

Case 2: custom projection to general functions of state.

```julia
ds = Systems.lorenz96(5)
projection(u) = [sum(u), sqrt(u[1]^2 + u[2]^2)]
complete_state(y) = repeat([y[1]/5], 5)
prods = # same as in above example...
```
