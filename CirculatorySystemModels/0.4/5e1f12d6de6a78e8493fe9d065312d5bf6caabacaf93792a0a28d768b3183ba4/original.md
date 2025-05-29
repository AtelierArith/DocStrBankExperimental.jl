`DrivenPressure(; name, fun, P=1.0)`

Implements a driven pressure source to a system modulated by a function provided.

Parameters are in the cm, g, s system. Pressure in mmHg. `Δp` is calculated in mmHg, `q` is calculated in cm^3/s (ml/s).

Named parameters:

`P`:     Constant pressure in mmHg

`fun`:   Function which modulates the input
