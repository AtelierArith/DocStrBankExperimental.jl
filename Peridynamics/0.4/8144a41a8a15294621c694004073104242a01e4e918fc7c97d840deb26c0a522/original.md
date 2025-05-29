```
precrack!(body, set_a, set_b; update_dmg=true)
```

Create a crack between two point sets by prohibiting interaction between points of different point sets. The points in `set_a` are not allowed to interact with points in `set_b`.

# Arguments

  * `body::AbstractBody`: [`Body`](@ref).
  * `set_a::Symbol`: The name of a point set of this body.
  * `set_b::Symbol`: The name of a point set of this body.

# Keywords

  * `update_dmg::Bool`: If `true`, the material points involved in the predefined crack are   initially damaged. If `false`, the bonds involved are deleted and the material points   involved with the predefined crack are not damaged in the reference results.   (default: `true`)

# Throws

  * Error if the body does not contain sets with name `set_a` and `set_b`.
  * Error if the point sets intersect and a point is included in both sets.

# Example

```julia-repl
julia> point_set!(body, :a, 1:2)

julia> point_set!(body, :b, 3:4)

julia> precrack!(body, :a, :b)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  3 point set(s):
    1000-point set `all_points`
    2-point set `a`
    2-point set `b`
  1 predefined crack(s)
```
