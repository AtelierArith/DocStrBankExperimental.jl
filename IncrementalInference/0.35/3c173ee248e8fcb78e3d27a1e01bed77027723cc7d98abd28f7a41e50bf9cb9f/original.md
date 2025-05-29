Returns the parametric measurement for a factor as a tuple (measurement, inverse covariance) for parametric inference (assuming Gaussian). Defaults to find the parametric measurement at field `Z`. Notes

  * Users should overload this method should their factor not default to `.Z<:ParametricType`.
  * First design choice was to restrict this function to returning coordinates

      * See https://github.com/JuliaRobotics/RoME.jl/issues/465
      * Pay attention to which tangent space point is used for converting points on a manifold to coordinates,

          * Originally written just for Lie Groups to support legacy, but future needs may well alter the design.
  * Original design driven by parametric solve and dead reckon tethering.

See also: [`accumulateFactorMeans`](@ref), [`solveFactorParametric`](@ref)
