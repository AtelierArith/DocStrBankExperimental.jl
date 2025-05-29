```
shadow_model(sat_pos::AbstractArray, sun_pos::AbstractArray, R_Sun::Number, R_Occulting::Number, t::Number, ShadowModel::ShadowModelType)
```

Computes the Lighting Factor of the Sun occur from the Umbra and Prenumbra of Earth's Shadow

# Arguments

  * `sat_pos::AbstractArray`: The current satellite position.
  * `sun_pos::AbstractArray`: The current Sun position.
  * `R_Sun::Number`: The radius of the Sun.
  * `R_Occulting::Number`: The radius of the Occulting Body.
  * `ShadowModel::ShadowModelType`: The Earth shadow model to use. Current Options – Cylindrical, Conical, Conical_Simplified, None

# Returns

  * `SVector{3}{Number}`: Inertial acceleration from the 3rd body
