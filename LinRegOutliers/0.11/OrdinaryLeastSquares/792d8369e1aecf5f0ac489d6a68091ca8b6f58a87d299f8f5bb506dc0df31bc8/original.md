```
wls(X, y, wts)

Estimate weighted least squares regression and create OLS object with estimated parameters.
```

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix.
  * `y::AbstractVector{Float64}`: Response vector.
  * `wts::AbstractVector{Float64}`: Weights vector.

# Examples

```julia-repl
julia> X = hcat(ones(24), phones[:,"year"]);
julia> y = phones[:,"calls"];
julia> w = ones(24)
julia> w[15:20] .= 0.0
julia> reg = wls(X, y, w)
julia> reg.betas
2-element Vector{Float64}:
 -63.481644325290425
   1.3040571939231453
```
