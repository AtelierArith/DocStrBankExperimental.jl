```julia
integrate(
    grid::ExtendableGrids.ExtendableGrid,
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand!,
    resultdim::Int64;
    T,
    kwargs...
) -> Union{Float64, Vector{Float64}}

```

Integration that returns total integral of an integrand of the signature

```
integrand!(result, qpinfo)
```

over the entities AT of the grid. Here, qpinfo allows to access information at the current quadrature point. The length of the result needs to be specified via resultdim.

Keyword arguments:

  * quadorder = specifies the quadrature order (default = 0)
  * regions = restricts integration to these regions (default = [] meaning all regions)
  * items = restricts integration to these item numbers (default = [] meaning all items)
  * time = sets the time to be passed to qpinfo (default = 0)
  * params = sets the params array to be passed to qpinfo (default = [])
