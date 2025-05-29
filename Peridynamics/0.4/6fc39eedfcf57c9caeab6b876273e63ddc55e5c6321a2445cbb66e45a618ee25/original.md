```
forcedensity_bc!(fun, body, set, dim)
```

Specify force density boundary condition for points of the set `set_name` in `body`. The value of the boundary condition is calculated with the function `fun` at every time step.

# Arguments

  * `fun::Function`: Condition function for the calculation of a value, should return a   `Float64`. If the condition function returns a `NaN`, then this value is ignored, which   can be used to turn conditions off after a specified period of time. This function   accepts one ore two positional arguments and is aware of the argument names.   Possible arguments and names:

      * `fun(t)`: The function will receive the current time `t` at every time step.   This makes it possible to specify conditions that change over time.
      * `fun(p, t)`: This function will be processed for every point of `set_name` and   receives the reference position of a point as `SVector{3}` and the current time `t`   at every time step. This makes it possible to specify conditions that   also depend on the position of a point.
  * `body::AbstractBody`: [`Body`](@ref) the condition is specified on.
  * `set_name::Symbol`: The name of a point set of this body.
  * `dim::Union{Integer,Symbol}`: Direction of the condition, either specified as Symbol or   integer.

      * x-direction: `:x` or `1`
      * y-direction: `:y` or `2`
      * z-direction: `:z` or `3`

# Throws

  * Error if the body does not contain a set with `set_name`.
  * Error if the direction is not correctly specified.
  * Error if function is not suitable as condition function and has the wrong arguments.

# Example

```julia-repl
julia> forcedensity_bc!(t -> 8000.0, body, :all_points, :x)

julia> forcedensity_bc!((p,t) -> p[1] * t, body, :all_points, :y)

julia> forcedensity_bc!(t -> t > 0.00001 ? 8000.0 : NaN, body, :all_points, :z)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  3 boundary condition(s):
    BC on force density: point_set=all_points, dim=1
    BC on force density: point_set=all_points, dim=3
    Pos.-dep. BC on force density: point_set=all_points, dim=2
```
