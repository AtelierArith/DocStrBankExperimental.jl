`MynardValve_Atrioventricular(; name, ρ, Mrg, Mst, Ann, Kvc, Kvo)`

Implements the Mynard description for flow across the atrioventricular valves, full description in [Mynard]. This valve description corresponds to the atrioventricular valves where interia is not considered.

Note: The minimum level of regurgitation has to be set to machine precision eps()

Parameters are in the cm, g, s system. Pressure in mmHg. Flow in cm^3/s (ml/s) p is scaled to ensure units are consistent throughout.

Named parameters:

name    name of the element `ρ`     Blood density in g/cm^3 `Mrg`   Level of regurgitation exhibited by a valve in DN `Mst`   Level of stenosis exhibited by a valve in DN `Ann`   Annulus area in cm^2 `Kvc`   Valve closing rate coefficent in  cm^2/(dynes*s) `Kvo`   Valve opening rate coefficent in cm^2/(dynes*s)

p is calculated in mmHg q is calculated in cm^3/s (ml/s)
