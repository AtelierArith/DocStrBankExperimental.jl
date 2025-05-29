```
monitor(sol::AbstractODESolution; vars=nothing, tspan=nothing)
```

A plot recipe for monitor the orbit of a particle and other physics quantities.

# Arguments

  * `sol::AbstractODESolution`: the solution returned by the ODE solver.

# Keywords

  * `vars`: the argument used to choose the variables to be plotted. Default value is [4, 5, 6].
  * `tspan::Tuple`: the span of time to be plotted. For example, tspan = (0, 1).

## vars

The usage of `vars` for this function is different from those in [`orbit`](@ref). It can only be a list and its length is equal to 3. The type of its elements must be Integer or Function. The form of a function is the same as those prescribed by `orbit`. For example,

```julia
Eₖ(xu) = mₑ*(xu[4]^2 + xu[5]^2 + xu[6]^2)/2
monitor(sol, vars=[1, 2, Eₖ])
```
