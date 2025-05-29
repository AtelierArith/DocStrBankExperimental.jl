`soil_mulch_water_balance(rain, eto, cf, ϑ, s, sh, sw, sstar, ks, β, n, zr, cws,                           ce, ct, μ, ϕ, zm, ϑh, km, g, dt)`

Computes the mulching and soil water balance.

# Arguments

  * `rain::Float64`: rainfall.
  * `eto::Float64`: reference evapotranspiration.
  * `cf::Float64`: crop cover fraction.
  * `ϑ::Float64`: mulching moisture.
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
  * `ϕ::Float64`: mulching porosity.
  * `ϑh::Float64`: threshold that stops mulch leakage and evaporation.
  * `km::Float64`: mulching percolation rate.
  * `g::Float64`: exponent of mulching percolation.
  * `dt::Float64`: time interval.
