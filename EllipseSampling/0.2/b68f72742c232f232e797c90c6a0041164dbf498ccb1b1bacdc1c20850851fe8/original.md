```
generate_N_clustered_points(num_points::Int, Γ::Matrix{Float64}, θmle::Vector{Float64}, ind1::Int, ind2::Int; 
    confidence_level::Float64=0.01, dof::Int=2, start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0)
```

An alternate way to call [`generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.)`](@ref), by supplying a square matrix Γ, the inverse of the Hessian of a log-likelihood function at its maximum likelihood estimate, indexes of the two variables of interest and the confidence level that represent a 2D ellipse approximation of the log-likelihood function.

# Arguments

  * `num_points`: a positive integer number of points to generate that are equally spaced on the ellipse.
  * `Γ`: a square matrix (2D) which is the inverse of the Hessian of a log-likelihood function at its maximum likelihood estimate.
  * `θmle`: the maximum likelihood estimate for the parameters.
  * `ind1`: index of the first parameter of interest (corresponds to the row and column index of `Γ`)
  * `ind2`: index of the second parameter of interest (corresponds to the row and column index of `Γ`).

# Keyword Arguments

  * `confidence_level`: the confidence level ∈ [0.0,1.0] at which the ellipse approximation is constructed. Default is `0.01`.
  * `dof`: integer degrees of freedom used for calculation of the asymptotic confidence threshold defining the ellipse. Default is `2`.
  * `start_point_shift`: a number ∈ [0.0,1.0]. Default is `rand()` (defined on [0.0,1.0]), meaning that, by default, every time this function is called a different set of points will be generated.
  * `sqrt_distortion`: a number ∈ [0.0,1.0]. Default is `0.0`, meaning that, by default, this function will evenly space points on the the ellipse `e` with respect to the parameter `t`.
