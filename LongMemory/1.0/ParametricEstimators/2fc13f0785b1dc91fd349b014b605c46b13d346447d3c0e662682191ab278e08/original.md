```
csa_llk(p::Real, q::Real, x::Array)
```

Computes the log-likelihood of the CSA process with parameters `p` and `q` given the data `x`.

# Arguments

  * `p::Real`: The first parameter of the CSA process.
  * `q::Real`: The second parameter of the CSA process.
  * `x::Array`: The data.

# Output

  * `llk::Real`: The log-likelihood of the CSA process with parameters `p` and `q` given the data `x`.

# Notes

This function computes the concentrated log-likelihood function of the CSA process with parameters `p` and `q` given the data `x`.

# Examples

```julia
julia> csa_llk(1.4, 1.8, randn(100,1))
```
