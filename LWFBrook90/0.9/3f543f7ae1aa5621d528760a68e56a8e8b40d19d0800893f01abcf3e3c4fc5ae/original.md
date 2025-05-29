```
get_soil_(symbols, simulation; depths_to_read_out_mm = nothing, days_to_read_out_d = nothing))
```

Returns a 2D DataFrame of soil variables with soil layers as columns and time steps as rows. Supports a number of variables:     - `:θ` (= `:theta`) = volumetric soil moisture values (m3/m3)     - `:ψ` (= `:psi`) = soil matric potential (kPa)     - `:W` = soil wetness (-)     - `:SWATI` = soil water volumes contained in discretized layers (mm)     - `:K` = soil hydraulic conductivities (mm/day)     - `:δ18O`, `:δ2H`, `:d18O`, `:d2H` = isotopic signatures (delta)     - `TRANI`, `RWU` = root water uptake flux from each cell (mm/day) The user can define timesteps as `days_to_read_out_d` or specific depths as `depths_to_read_out_mm`, that are both optionally provided as numeric vectors, e.g. `depths_to_read_out_mm = [100, 150]` or `days_to_read_out_d = 1:1.0:100`

Function to read out soil variables from a simulated simulation.

  * `symbols`: can be a single symbol (:θ) or a vector of symbols [:θ] or [:θ, :ψ, :δ18O, :δ2H, :W, :SWATI, :K]

      * Please note that also non-Unicode symbols are accepted: e.g. [:theta, :psi, :delta18O, :delta2H, :d18O, :d2H]
  * `simulation`: is a `DiscretizedSPAC` that has been simulated.
  * `depths_to_read_out_mm`: either `nothing` or vector of Integers.
  * `days_to_read_out_d`: either  `nothing` or vector of Floats representing days.

Examples     get*soil*(:θ, simulation)     get*soil*([:θ, :ψ, :K], simulation; depths*to*read*out*mm = [100, 200, 500, 1200])
