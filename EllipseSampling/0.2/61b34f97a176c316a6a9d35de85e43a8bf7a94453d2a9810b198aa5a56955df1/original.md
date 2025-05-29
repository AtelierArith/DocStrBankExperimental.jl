```
generate_perimeter_point(norm_distance_on_perimeter::Float64, Γ::Matrix{Float64}, θmle::Vector{Float64}, ind1::Int, ind2::Int; confidence_level::Float64=0.01)
```

An alternate way to call [`generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)`](@ref), by supplying a square matrix Γ, the inverse of the Hessian of a log-likelihood function at its maximum likelihood estimate, indexes of the two variables of interest and the confidence level that represent a 2D ellipse approximation of the log-likelihood function.

# Arguments

  * `norm_distance_on_perimeter`: a number ∈ [0.0,1.0] which represents the normalised distance on the perimeter of an ellipse. A value of 0.5 corresponds to a point halfway along the ellipse's perimeter, while a value of 0.7 corresponds to a point 70% along the ellipse's perimeter.
  * `Γ`: a square matrix (2D) which is the inverse of the Hessian of a log-likelihood function at its maximum likelihood estimate.
  * `θmle`: the maximum likelihood estimate for the parameters.
  * `ind1`: index of the first parameter of interest (corresponds to the row and column index of `Γ`)
  * `ind2`: index of the second parameter of interest (corresponds to the row and column index of `Γ`).

# Keyword Arguments

  * `confidence_level`: the confidence level ∈ [0.0,1.0] at which the ellipse approximation is constructed. Default is `0.01`.
