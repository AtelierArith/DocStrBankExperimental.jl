```
contact!(multibody_setup, name_body_a, name_body_b; kwargs...)
```

Define a short range force contact between body `name_body_a` and `name_body_b` in the [`MultibodySetup`](@ref) `multibody_setup`.

# Arguments

  * `multibody_setup::MultibodySetup`: [`MultibodySetup`](@ref).
  * `name_body_a::Symbol`: The name of a body in this multibody setup.
  * `name_body_b::Symbol`: The name of a body in this multibody setup.

# Keywords

  * `radius::Float64`: Contact search radius. If a the distance of a point in body   `name_body_a` and a point in body `name_body_b` is lower than this radius, a contact   force is calculated. This radius should be in the order of the point spacing of a   point cloud.
  * `penalty_factor::Float64`: Penalty factor for the short range force contact algorithm.   (default: `1e12`)

# Throws

  * Error if `multibody_setup` does not contain bodies with name `name_body_a` and   `name_body_b`.
  * Error if the keyword `radius` is not specified or `radius ≤ 0`.
  * Error if `penalty_factor ≤ 0`.

# Examples

```julia-repl
julia> ms = MultibodySetup(:a => body_a, :b => body_b)
2000-point MultibodySetup:
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  1000-point Body{BBMaterial{NoCorrection}} with name `b`

julia> contact!(ms, :a, :b; radius=0.001)

julia> ms
2000-point MultibodySetup:
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  2 short range force contact(s)
```
