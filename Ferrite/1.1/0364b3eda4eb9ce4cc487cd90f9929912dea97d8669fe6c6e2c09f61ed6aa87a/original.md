```
InterfaceValues
```

An `InterfaceValues` object facilitates the process of evaluating values, averages, jumps and gradients of shape functions and function on the interfaces between elements.

The first element of the interface is denoted "here" and the second element "there".

**Constructors**

  * `InterfaceValues(qr::FacetQuadratureRule, ip::Interpolation)`: same quadrature rule and interpolation on both sides, default linear Lagrange geometric interpolation.
  * `InterfaceValues(qr::FacetQuadratureRule, ip::Interpolation, ip_geo::Interpolation)`: same as above but with given geometric interpolation.
  * `InterfaceValues(qr_here::FacetQuadratureRule, ip_here::Interpolation, qr_there::FacetQuadratureRule, ip_there::Interpolation)`: different quadrature rule and interpolation on the two sides, default linear Lagrange geometric interpolation.
  * `InterfaceValues(qr_here::FacetQuadratureRule, ip_here::Interpolation, ip_geo_here::Interpolation, qr_there::FacetQuadratureRule, ip_there::Interpolation, ip_geo_there::Interpolation)`: same as above but with given geometric interpolation.
  * `InterfaceValues(fv::FacetValues)`: quadrature rule and interpolations from facet values (same on both sides).
  * `InterfaceValues(fv_here::FacetValues, fv_there::FacetValues)`: quadrature rule and interpolations from the facet values.

**Associated methods:**

  * [`shape_value_average`](@ref)
  * [`shape_value_jump`](@ref)
  * [`shape_gradient_average`](@ref)
  * [`shape_gradient_jump`](@ref)

**Common methods:**

  * [`reinit!`](@ref)
  * [`getnquadpoints`](@ref)
  * [`getdetJdV`](@ref)
  * [`shape_value`](@ref)
  * [`shape_gradient`](@ref)
  * [`shape_divergence`](@ref)
  * [`shape_curl`](@ref)
  * [`function_value`](@ref)
  * [`function_gradient`](@ref)
  * [`function_symmetric_gradient`](@ref)
  * [`function_divergence`](@ref)
  * [`function_curl`](@ref)
  * [`spatial_coordinate`](@ref)
