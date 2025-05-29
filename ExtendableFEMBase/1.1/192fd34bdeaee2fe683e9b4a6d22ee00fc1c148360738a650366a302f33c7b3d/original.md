```
function ExtendableGrids.interpolate!(target::FEVectorBlock,
	 AT::Type{<:AssemblyType},
	 source!::Function;
	 items = [],
	 bonus_quadorder = 0,
	 time = 0,
	 kwargs...)
```

Interpolates the given source into the finite elements space assigned to the target FEVectorBlock with the specified AssemblyType (usually ON_CELLS). 

The source functions should adhere to the interface

```julia
	source!(result, qpinfo)
```

The qpinfo argument communicates vast information of the current quadrature/evaluation point.

The bonus_quadorder argument can be used to steer the quadrature order of integrals that needs to be computed for the interpolation (the default quadrature order corresponds to the polynomial order of the finite element).
