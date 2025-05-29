```
FDEsolver(F::Function, tSpan::Vector{<:Real}, y0::Union{Real, Vector{<:Real}, Matrix{<:Real}}, β::Union{Real, Vector{<:Real}}, par...; h = 2^-6, nc = 2, JF = nothing, tol = 1e-6, itmax = 100)
```

Solves fractional differential equations with a predictor-corrector approach.

# Arguments

  * `F::Function`: the right side of the system of differential equations. It must be expressed  in the form of a function and return a vector function with the same number of  entries of order of derivatives. This function can also include a vector of  parameters: `par...` .
  * `tSpan::Vector{<:Real}`: the time span along which computation is performed.
  * `y0::Union{Real, Vector{<:Real}, Matrix{<:Real}}`: the initial values in the form of a  row vector (`Vector{<:Real}`) for $β <= 1$ and a matrix (`Matrix{<:Real}`) for $β > 1$,  where each column corresponds to the initial values of one differential equation and  each row to the order of derivation.
  * `β::Union{Real, Vector{<:Real}}`: the orders of derivation in the form of a row vector, where  each element corresponds to the order of one differential equation. It can take  decimal as well as integer values.
  * `JF::Function`: the Jacobian of F. If not provided, the solver will evaluate the solution  without the aid of the Jacobian matrix.
  * `par...`: additional parameters for the function F.
  * `h::Real`: the step size of the computation.
  * `nc::Int64`: the desired number of corrections for predictor-corrector method, when there is no Jacobian.
  * `tol::Float64`: the tolerance of errors, the norm inf of each iteration (for NR method) or correction when nc>10 (for PC method).
  * `ìtmax::Int64`: the maximal number of iterations.
