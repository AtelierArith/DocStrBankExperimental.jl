```
function ExtendableGrids.interpolate!(target::FEVectorBlock,
	 source::Function;
	 items = [],
	 bonus_quadorder = 0,
	 time = 0,
	 kwargs...)
```

Interpolates the given source function into the finite element space assigned to the target FEVectorBlock. 

The source functions should adhere to the interface

```julia
	source!(result, qpinfo)
```

The qpinfo argument communicates vast information of the current quadrature/evaluation point.

The bonus_quadorder argument can be used to steer the quadrature order of integrals that needs to be computed for the interpolation (the default quadrature order corresponds to the polynomial order of the finite element).
