```
FacetValues([::Type{T}], quad_rule::FacetQuadratureRule, func_interpol::Interpolation, [geom_interpol::Interpolation])
```

A `FacetValues` object facilitates the process of evaluating values of shape functions, gradients of shape functions, values of nodal functions, gradients and divergences of nodal functions etc. on the facets of finite elements.

**Arguments:**

  * `T`: an optional argument (default to `Float64`) to determine the type the internal data is stored as.
  * `quad_rule`: an instance of a [`FacetQuadratureRule`](@ref)
  * `func_interpol`: an instance of an [`Interpolation`](@ref) used to interpolate the approximated function
  * `geom_interpol`: an optional instance of an [`Interpolation`](@ref) which is used to interpolate the geometry. By default linear Lagrange interpolation is used.

**Keyword arguments:** The following keyword arguments are experimental and may change in future minor releases

  * `update_gradients`: Specifies if the gradients of the shape functions should be updated (default true)
  * `update_hessians`: Specifies if the hessians of the shape functions should be updated (default false)

**Common methods:**

  * [`reinit!`](@ref)
  * [`getnquadpoints`](@ref)
  * [`getdetJdV`](@ref)
  * [`shape_value`](@ref)
  * [`shape_gradient`](@ref)
  * [`shape_symmetric_gradient`](@ref)
  * [`shape_divergence`](@ref)
  * [`function_value`](@ref)
  * [`function_gradient`](@ref)
  * [`function_symmetric_gradient`](@ref)
  * [`function_divergence`](@ref)
  * [`spatial_coordinate`](@ref)
