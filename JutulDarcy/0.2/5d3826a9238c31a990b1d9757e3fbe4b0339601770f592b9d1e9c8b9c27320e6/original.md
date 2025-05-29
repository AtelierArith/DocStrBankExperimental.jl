```
compute_peaceman_index(Δ, K, radius; kwargs...)
```

Compute the Peaceman well index for a given grid block.

# Arguments

  * `Δ`: The grid block size as a tuple `(dx, dy, dz)`
  * `K`: The permeability of the medium (Matrix for full tensor, or scalar).
  * `radius`: The well radius.

# Keyword Arguments

  * `dir::Symbol = :z`: Direction of the well, can be `:x`, `:y`, or `:z`.
  * `net_to_gross = 1.0`: Net-to-gross ratio, used to scale the value for vertical directions.
  * `constant = 0.14`: Constant used in the calculation of the equivalent radius. TPFA specific.
  * `Kh = nothing`: Horizontal permeability, if not provided, it will be computed.
  * `drainage_radius = nothing`: Drainage radius, if not provided, it will be computed.
  * `skin = 0`: Skin factor, used to account for near-wellbore effects.
  * `check = true`: Flag to check for negative well index values.

# Returns

  * `Float64`: The computed Peaceman well index.
