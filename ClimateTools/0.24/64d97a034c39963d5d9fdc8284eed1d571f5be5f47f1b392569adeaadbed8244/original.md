vaporpressure(surface*pressure::ClimGrid, specific*humidity::ClimGrid)

Returns the vapor pressure (vp) (Pa) based on the surface pressure (sp) (Pa) and the specific humidity (q).

$vp = \frac{q * sp}{q+0.622}$
