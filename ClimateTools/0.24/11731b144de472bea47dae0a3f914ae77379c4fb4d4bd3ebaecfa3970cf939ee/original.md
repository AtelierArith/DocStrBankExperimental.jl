approx*surfacepressure(sealevel*pressure::ClimGrid, orography::ClimGrid, daily_temperature::ClimGrid)

Returns the approximated surface pressure (*sp*) (Pa) using sea level pressure (*psl*) (Pa), orography (*orog*) (m), and daily mean temperature (*tas*) (K).

$sp = psl * 10^{x}$

where $x = \frac{-orog}{18400 * tas / 273.15}$
