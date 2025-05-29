```
auxiliary_vars(::SnowModel)
```

Returns the auxiliary variable names for the snow model. These include the specific humidity at the surface of the snow `(`q*sfc`, unitless), the mass fraction in liquid water (`q*l`, unitless), the thermal conductivity (`κ`, W/m/K), the bulk temperature (`T`, K), the surface temperature (`T*sfc`, K), the snow depth (`z*snow`, m), the bulk snow density (`ρ*snow`, kg/m^3) the SHF, LHF, and vapor flux (`turbulent*fluxes.shf`, etc), the net radiation (`R*n, J/m^2/s)`, the energy flux in liquid water runoff (`energy*runoff`, J/m^2/s), the water volume in runoff (`water_runoff`, m/s), and the total energy and water fluxes applied to the snowpack.

Since the snow can melt completely in one timestep, we clip the water and energy fluxes such that SWE cannot become negative and U cannot become unphysical. The clipped values are what are actually applied as boundary fluxes, and are stored in `applied_` fluxes.
