```
velocity_ic!(body, set_name, dim, value)
velocity_ic!(fun, body, set_name, dim)
```

Specify velocity initial condition for points of the set `set_name` in `body`. The `value` of the initial condition is specified before time integration. If a function `fun` is specified, then the value is with that function.

# Arguments

  * `body::AbstractBody`: [`Body`](@ref) the condition is specified on.
  * `set_name::Symbol`: The name of a point set of this body.
  * `dim::Union{Integer,Symbol}`: Direction of the condition, either specified as Symbol or   integer.

      * x-direction: `:x` or `1`
      * y-direction: `:y` or `2`
      * z-direction: `:z` or `3`
  * `value::Real`: Value that is specified before time integration.
  * `fun::Function`: Condition function for the calculation of a value, should return a   `Float64`. If the condition function returns a `NaN`, then this value is ignored, which   can be used to turn off the condition for a specified position. This function   accepts one ore two positional arguments and is aware of the argument names.   Possible arguments and names:

      * `fun(p)`: The function will receive the reference position `p` of a point as   `SVector{3}`.

# Throws

  * Error if the body does not contain a set with `set_name`.
  * Error if the direction is not correctly specified.
  * Error if function is not suitable as condition function and has the wrong arguments.

# Example

```julia-repl
julia> velocity_ic!(body, :all_points, :x, -100.0)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1 initial condition(s):
    IC on velocity: point_set=all_points, dim=1
```
