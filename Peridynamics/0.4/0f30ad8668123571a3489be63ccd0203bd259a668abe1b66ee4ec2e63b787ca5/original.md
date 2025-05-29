```
n_points(body)
```

Return the total number of points in a body.

# Arguments

  * `body::Body`: [`Body`](@ref).

# Returns

  * `n_points::Int`: The number of points in the body.

# Examples

```julia-repl
julia> body = Body(BBMaterial(), pos, vol)
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`

julia> n_points(body)
1000
```

---

```
n_points(multibody_setup)
```

Return the total number of points in a multibody setup.

# Arguments

  * `multibody_setup::MultibodySetup`: [`MultibodySetup`](@ref).

# Returns

  * `n_points::Int`: The sum of all points from all bodies in the multibody setup.

# Examples

```julia-repl
julia> ms = MultibodySetup(:a => body_a, :b => body_b)
2000-point MultibodySetup:
  1000-point Body{BBMaterial{NoCorrection}} with name `a`
  1000-point Body{BBMaterial{NoCorrection}} with name `b`

julia> n_points(ms)
2000
```
