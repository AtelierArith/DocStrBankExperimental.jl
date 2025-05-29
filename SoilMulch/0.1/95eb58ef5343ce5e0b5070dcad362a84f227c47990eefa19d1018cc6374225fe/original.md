`cover_fraction(cf, t, tr, cmax, r, γ, tsen)`

Compute crop cover fraction.

# Arguments

  * `cf::Float64`: crop cover fraction.
  * `t::Float64`: time [days].
  * `tr::Float64`: plant transpiration.
  * `cmax::Float64`: maximum crop cover fraction.
  * `r::Float64`: parameter of cover fraction model.
  * `γ::Float64`: slope of increase senescence after tsen.
  * `tsen::Float64`: senescence time.

If plant transpiration is not available, use ETo.
