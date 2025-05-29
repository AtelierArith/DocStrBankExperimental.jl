`ShiValve(; name, CQ, Kp, Kf, Kb, Kv, θmax, θmin)`

Implements the Shi description for valve opening and closing, full description in [Shi].

Parameters are in the cm, g, s system. Pressure in mmHg. Flow in cm^3/s (ml/s) Maximum and Minimum angles given in rad, to convert from degrees multiply angle by pi/180.

Named parameters:

`CQ`    Flow coefficent in ml/(s*mmHg^0.5)

`Kp`    Pressure effect on the valve in rad/(s^2*mmHg)

`Kf`    Frictional effect on the valve in 1/s

`Kb`    Fluid velocity effect on the valve in rad/(s*m)

`Kv`    Vortex effect on the valve in rad/(s*m)

`θmax`  Valve maximum opening angle in rad

`θmin`  Valve minimum opening angle in rad
