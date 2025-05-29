`MynardValve_SemiLunar(; name, ρ, Leff, Mrg, Mst, Ann, Kvc, Kvo)`

Implements the Mynard description for flow across the semilunar valves, full description in [Mynard]. This valve description corresponds to the semilunar valves where interia is an effect we consider.

Note: The minimum level of regurgitation has to be set to machine precision eps()

Parameters are in the cm, g, s system. Pressure in mmHg. Flow in cm^3/s (ml/s) p is scaled to ensure units are consistent throughout.

Named parameters:

name    name of the element `ρ`     Blood density in g/cm^3 `Leff`  An effective length in cm `Mrg`   Level of regurgitation exhibited by a valve in DN `Mst`   Level of stenosis exhibited by a valve in DN `Ann`   Annulus area in cm^2 `Kvc`   Valve closing rate coefficent in  cm^2/(dynes*s) `Kvo`   Valve opening rate coefficent in cm^2/(dynes*s)

p is calculated in mmHg q is calculated in cm^3/s (ml/s)
