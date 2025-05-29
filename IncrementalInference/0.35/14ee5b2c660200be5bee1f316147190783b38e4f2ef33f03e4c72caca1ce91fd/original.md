Sample the factor in `CalcFactor`. A default `getSample` method is provided that should cover most use cases,  if more advanced sampling is required, the `getSample` function should be extended.

The default behavior for `getSample` is as follows:

  * The `SamplableBelief``shall be in the field`Z`and that shall be enough to fully define the factor, i.e.`Z<:SamplableBelief` should be the only field.
  * Sampling on `<:AbstractManifoldMinimize` factors defined on Group Manifolds: 

      * `getSample` normally returns a tangent vector at the identity element, however it should just match the custom factor definition.
  * Sampling on prior (`<:AbstractPrior`) factors : 

      * `getSample` must return a point on the manifold that matches the point representation of the variable.

Notes

  * Users should overload this method should their factor not only use field `Z` for the `SamplableBelief`.
  * See the Custom Factors section in the Caesar.jl documentation for more examples and details.
  * Also see issue https://github.com/JuliaRobotics/IncrementalInference.jl/issues/1441

See also: [`getMeasurementParametric`](@ref)
