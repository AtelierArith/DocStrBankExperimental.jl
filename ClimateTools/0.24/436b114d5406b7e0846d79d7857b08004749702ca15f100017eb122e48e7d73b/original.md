vaporpressure(specific*humidity::ClimGrid, sealevel*pressure::ClimGrid, orography::ClimGrid, daily_temperature::ClimGrid)

Returns the vapor pressure (vp) (Pa) estimated with the specific humidity (q), the sea level pressure (psl) (Pa), the orography (orog) (m) and the daily mean temperature (tas) (K). An approximation of the surface pressure is first computed by using the sea level pressure, orography and the daily mean temperature (see [`approx_surfacepressure`](@ref)). Then, vapor pressure is calculated by:

$vp = \frac{q * sp}{q+0.622}$
