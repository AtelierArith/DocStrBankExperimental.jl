```
MultibodySetup(body_pairs...)
```

Setup for a peridynamic simulation with multiple bodies.

# Arguments

  * `body_pairs::Pair{Symbol,<:AbstractBody}`: Pairs of `:body_name => body_object`.   The name of the body has to be specified as a Symbol.

# Throws

  * Error if less than 2 bodies are defined.

# Examples

```julia-repl
julia> sphere = Body(BBMaterial(), pos_sphere, vol_sphere)
280-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    280-point set `all_points`

julia> plate = Body(BBMaterial(), pos_plate, vol_plate)
25600-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    25600-point set `all_points`

julia> ms = MultibodySetup(:sphere => sphere, :plate => plate)
25880-point MultibodySetup:
  280-point Body{BBMaterial{NoCorrection}} with name `sphere`
  25600-point Body{BBMaterial{NoCorrection}} with name `plate`
```

---

!!! warning "Internal use only"
    Please note that the fields are intended for internal use only. They are *not* part of the public API of Peridynamics.jl, and thus can be altered (or removed) at any time without it being considered a breaking change.


```julia
MultibodySetup{Bodies}
```

# Type Parameters

  * `Bodies <: Tuple`: All types of the different bodies in the multibody setup.

# Fields

  * `bodies::Bodies`: A Tuple containing all the bodies.
  * `body_names::Vector{Symbol}`: All body names.
  * `body_idxs::Dict{Symbol,Int}`: A Dict to get the body index with the body name.
  * `srf_contacts::Vector{ShortRangeForceContact}`: All short range force contacts.
