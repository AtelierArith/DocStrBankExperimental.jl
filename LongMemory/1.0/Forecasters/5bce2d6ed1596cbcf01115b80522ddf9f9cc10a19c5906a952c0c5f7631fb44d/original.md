```
csa_ma_coefs(p::Real, q::Real, maxlags::Int)
```

Computes the MA coefficients of the CSA process with parameters `p` and `q` at lags 0, ..., `maxlags-1`.

# Arguments

  * `p::Real`: The parameter p of the CSA process.
  * `q::Real`: The parameter q of the CSA process.
  * `maxlags::Int`: The number of lags to compute.

# Output

  * `ma_coefs::Array`: The MA coefficients of the CSA process with parameters `p` and `q` at lags 0, ..., `maxlags-1`.

# Notes

The MA coefficients are computed using the recursive formula for speed. The zero lag coefficient is included, it is theoretically 1.

# Examples

```julia
julia> csa_ma_coefs(1.4, 1.4, 5)
```
