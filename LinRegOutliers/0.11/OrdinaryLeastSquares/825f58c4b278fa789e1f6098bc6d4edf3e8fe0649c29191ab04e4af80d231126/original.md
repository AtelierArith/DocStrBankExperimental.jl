```
ols(X, y)

Create OLS object with estimated regression coefficients.
```

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix.
  * `y::AbstractVector{Float64}`: Response vector.

# Examples

```julia-repl
julia> X = hcat(ones(24), phones[:,"year"]);
julia> y = phones[:,"calls"];
julia> reg = ols(X, y)
julia> reg.betas
2-element Vector{Float64}:
 -260.0592463768119
    5.04147826086957
```
