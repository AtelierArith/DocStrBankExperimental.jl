```
elasticitySubCompGeneral(labor_input::AbstractArray{<:Real}, z::Real, b_g::Function, e_h::Vector{Function}; MPL=nothing, xT=nothing, q=nothing) -> (AbstractArray{<:Real}, AbstractArray{<:Real})
```

Calculates the elasticity of substitution and complementarity for a given set of parameters.

# Arguments

  * `labor_input`: An array of labor inputs of different types with H elements. If `nothing`, it will be computed internally given xT and q.
  * `z`: Productivity parameter.
  * `b_g`: General task density function.
  * `e_h`: Vector of comparative advantage functions.
  * `MPL`: (optional) An array representing the marginal productivity of labor. If not provided, it will be computed within the function.
  * `xT`: (optional) An array representing precomputed task thresholds. If not provided, it will be computed within the function.

-`q`: (optional) A scalar of total output produced. If not provided, it will be computed within the function.

# Returns

  * `ϵ_h_sub`: Matrix of elasticity of substitution values for each worker type h (rows) relative to worker type h_prime (columns).
  * `ϵ_h_compl`: Matrix of elasticity of complementarity values for each worker type h (rows) relative to worker type h_prime (columns).
