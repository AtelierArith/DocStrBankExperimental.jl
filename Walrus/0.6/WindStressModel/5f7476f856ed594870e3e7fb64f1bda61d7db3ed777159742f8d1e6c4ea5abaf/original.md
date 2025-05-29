```
LogarithmicNeutralWind(; monin_obukhov_stability_length = 0.4
                         charnock_coefficient = 0.014
                         air_kinematic_viscosity = 1.488e-5
                         gravity_wave_coefficient = 0.11
                         gravity = g_Earth,

                         precompute_drag_coefficients = false,
                         precompute_wind_speeds = [0:25/100000:25;],
                         arch = CPU())
```

Returns a `LogarithmicNeutralWind` parameterisation for the surface drag coefficient

$C_d$ is parameterised as,

$$
C_d = \left(\frac{\kappa}{\log{\frac{10}{z_0}}}\right)^2,
$$

where $\kappa$ is the Monin‐Obukhov stability length and $z_0$ is the velocity  roughness length. This is the roughness length scale which logarithmically brings  the relative velocity to zero at the surface, i.e.

$$
U=\frac{u\star}{\kappa}\log\frac{z}{z_0},
$$

where $u\star$ is the friction velocity. Additionally $z_0$ is given as,

$$
z_0=b\frac{\nu}{u\star} + \frac{a_c}{g}u\star^2,
$$

where $\nu$ is the kinematic viscosity of air and g is the acceleration of gravity.

This model itterativly solves these equations to find $z_0$. Alternativly, if the flag  `precomputed_roughness_length` is set to they are pre computed at `precompute_wind_speeds`  between which $z_0$ is then interpolated during run time. Precomputed velocities are  converted to appropriate types for `arch` (i.e. `CPU()` or `GPU()`)

This parameterisaion is described in [smith1988](@citet)
