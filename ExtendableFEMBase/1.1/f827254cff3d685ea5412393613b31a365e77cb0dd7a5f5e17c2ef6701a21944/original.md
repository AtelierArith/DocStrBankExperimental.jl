```julia
integrate!(
    integral4items::AbstractArray{T},
    grid::ExtendableGrids.ExtendableGrid{Tv, Ti},
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand;
    offset,
    bonus_quadorder,
    quadorder,
    regions,
    time,
    items,
    force_quadrature_rule,
    kwargs...
)

```

Integration of an integrand of the signature

```
integrand!(result, qpinfo)
```

over the entities AT of the grid. The result on every item is written into integral4items (at least of size nitems x length of result). As usual, qpinfo allows to access information at the current quadrature point.

Keyword arguments:

  * quadorder = specifies the quadrature order (default = 0)
  * regions = restricts integration to these regions (default = [] meaning all regions)
  * items = restricts integration to these item numbers (default = [] meaning all items)
  * time = sets the time to be passed to qpinfo (default = 0)
  * params = sets the params array to be passed to qpinfo (default = [])
  * offset = offset for writing into result array integral4items (default = [0]),
