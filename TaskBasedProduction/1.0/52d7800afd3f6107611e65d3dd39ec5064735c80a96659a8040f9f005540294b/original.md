```
unitInputDemand(xT::AbstractArray{<:Real}, θ::Real, κ::Real, z::Real, αVec::AbstractArray{<:Real}, skipParamChecks::Bool = false) -> AbstractArray{<:Real}
```

Calculates unit labor demands given blueprint scale `θ`, blueprint shape `κ`, productivity `z`, an array of comparative advantage values `αVec` with H elements (one for each worker type), and an array `xT` of H-1 thresholds in task space.

# Arguments

  * `xT`: An array of H-1 thresholds in task space.
  * `q`: Quantity produced
  * `θ`: Blueprint scale parameter.
  * `κ`: Blueprint shape parameter.
  * `z`: Productivity parameter.
  * `αVec`: An array of comparative advantage values with H elements.
  * `skipParamChecks`: A boolean indicating whether to skip parameter checks (default is false).

# Returns

  * An array representing the labor demand for each labor type.
