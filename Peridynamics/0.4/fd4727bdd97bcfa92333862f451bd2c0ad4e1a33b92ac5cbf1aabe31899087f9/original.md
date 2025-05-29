```
no_failure!(body::AbstractBody, set_name::Symbol)
no_failure!(body::AbstractBody)
```

Disallow failure for all points of the point set `set_name` of the `body`. If no `set_name` is specified, failure is prohibited for the whole `body`.

# Arguments

  * `body::AbstractBody`: [`Body`](@ref) for which failure is prohibited.
  * `set_name::Symbol`: The name of a point set of this body.

!!! danger "Overwriting failure permission with `material!` and `no_failure!`"
    The function `material!` sets failure permissions due to the provided input parameters, so if it is used afterwards, previously set failure prohibitions might be overwritten!


# Throws

  * Error if the body does not contain a set with `set_name`.

# Examples

```julia-repl
julia> no_failure!(body)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1000 points with failure prohibited
```
