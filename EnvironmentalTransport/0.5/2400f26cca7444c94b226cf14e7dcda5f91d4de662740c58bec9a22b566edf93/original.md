Create an `EarthSciMLBase.Operator` that performs advection. Advection is performed using the given `stencil` operator (e.g. `l94_stencil` or `ppm_stencil`). `p` is an optional parameter set to be used by the stencil operator. `bc_type` is the boundary condition type, e.g. `ZeroGradBC()`.

Wind field data will be added in automatically if available. Currently the only valid source of wind data is `EarthSciData.GEOSFP`.
