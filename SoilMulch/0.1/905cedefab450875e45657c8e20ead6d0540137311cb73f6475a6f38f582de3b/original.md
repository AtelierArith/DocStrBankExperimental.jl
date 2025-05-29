`soil_water_balance(rain, eto, cf, s, sh, sw, sstar, ks, β, n, zr, rth, ce, ct, dt)`

Computes the soil water balance under no mulching conditions.

# Arguments

  * `rain::Float64`: rainfall.
  * `eto::Float64`: reference evapotranspiration.
  * `cf::Float64`: crop cover fraction.
  * `s::Float64`: soil moisture.
  * `sh::Float64`: soil moisture at wilting point.
  * `sw::Float64`: soil moisture at wilting point.
  * `sstar::Float64`: soil moisture below the field capacity.
  * `ks::Float64`: saturated hydraulic conductivity.
  * `β::Float64`: exponent of hydraulic conductivity curve.
  * `n::Float64`: soil porosity.
  * `zr::Float64`: root depth.
  * `cws::Float64`: canopy water storage capacity.
  * `ce::Float64`: baseline evaporation coefficient.
  * `ct::Float64`: baseline transpiration factor.
  * `dt::Float64`: time interval.
