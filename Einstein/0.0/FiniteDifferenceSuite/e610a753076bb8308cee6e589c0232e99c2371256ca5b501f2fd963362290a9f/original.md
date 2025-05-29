```
fdm_weights_fornberg([TR=Float64], order::Integer, x0::Real, x::AbstractVector; 
                         hermite::Bool=false)
```

Calculate finite difference weights for arbitrary-order derivatives using the Fornberg algorithm. Taken from [SciML/MethodOfLines.jl](https://github.com/SciML/MethodOfLines.jl).

# Arguments

  * `TR`: Type parameter for the weights (defaults to type of x0)
  * `order`: Order of the derivative to approximate
  * `x0`: Point at which to approximate the derivative
  * `x`: Grid points to use in the approximation
  * `hermite`: Whether to include first derivative values (Hermite finite differences)

# Returns

If `hermite == false`:

  * `Vector{TR}`: Weights for standard finite differences

If `hermite == true`:

  * `Tuple{Vector{TR}, Vector{TR}}`: Weights for Hermite finite differences

# Requirements

  * For standard finite differences: N > order
  * For Hermite finite differences: N > order/2 + 1

where N is the length of x

# Examples

```julia
# Standard central difference for first derivative
x = [-1.0, 0.0, 1.0]
w = fdm_weights_fornberg(1, 0.0, x)
# Returns approximately [-0.5, 0.0, 0.5]

# Forward difference for second derivative
x = [0.0, 1.0, 2.0, 3.0]
w = fdm_weights_fornberg(2, 0.0, x)

# Hermite finite difference for third derivative
x = [-1.0, 0.0, 1.0]
w_f, w_d = fdm_weights_fornberg(3, 0.0, x, hermite=true)
```

# References

  * [MethodOfLines.jl/src/discretization/schemes/fornberg*calculate*weights.jl at master · SciML/MethodOfLines.jl](https://github.com/SciML/MethodOfLines.jl/blob/master/src/discretization/schemes/fornberg_calculate_weights.jl)
  * [fornberg1988generation](@citet*)
  * [fornberg2021algorithm](@citet*)
  * [Fornberg1998](@citet*)
  * [precision - Numerical derivative and finite difference coefficients: any update of the Fornberg method? - Computational Science Stack Exchange](https://scicomp.stackexchange.com/questions/11249/numerical-derivative-and-finite-difference-coefficients-any-update-of-the-fornb)
