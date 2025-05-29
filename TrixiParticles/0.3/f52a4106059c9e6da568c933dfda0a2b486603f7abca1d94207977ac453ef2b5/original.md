```
AkinciFreeSurfaceCorrection(rho0)
```

Free surface correction according to [Akinci et al. (2013)](@cite Akinci2013). At a free surface, the mean density is typically lower than the reference density, resulting in reduced surface tension and viscosity forces. The free surface correction adjusts the viscosity, pressure, and surface tension forces near free surfaces to counter this effect. It's important to note that this correlation is unphysical and serves as an approximation. The computation time added by this method is about 2–3%.

Mathematically the idea is quite simple. If we have an SPH particle in the middle of a volume at rest, its density will be identical to the rest density $\rho_0$. If we now consider an SPH particle at a free surface at rest, it will have neighbors missing in the direction normal to the surface, which will result in a lower density. If we calculate the correction factor

$$
k = \rho_0/\rho_\text{mean},
$$

this value will be about ~1.5 for particles at the free surface and can then be used to increase the pressure and viscosity accordingly.

# Arguments

  * `rho0`: Rest density.
