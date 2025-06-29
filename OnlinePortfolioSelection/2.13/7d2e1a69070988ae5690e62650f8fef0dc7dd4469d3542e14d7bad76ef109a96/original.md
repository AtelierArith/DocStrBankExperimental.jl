```
maeg(x::AbstractMatrix, w::Integer, H::AbstractVector)
```

Run Moving-window-based Adaptive Exponential Gradient (MAEG) algorithm.

# Arguments

  * `x::AbstractMatrix`: A matrix of price relatives of `n_assets` over `n_periods`.
  * `w::Integer`: The window size.
  * `H::AbstractVector`: A vector of learning rates.

# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

!!! warning "Beware!"
    `x` should be a matrix of size `n_assets` × `n_periods`.


# Example

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(4, 10);

julia> w = 3;

julia> H = [0.01, 0.02, 0.2];

julia> m = maeg(rel_pr, w, H);

julia> m.b
4×10 Matrix{Float64}:
 0.25  0.250307  0.25129   0.251673  0.250823  0.267687  0.313794  0.319425  0.378182  0.427249
 0.25  0.249138  0.248921  0.249289  0.250482  0.23192   0.202576  0.179329  0.160005  0.168903
 0.25  0.250026  0.250656  0.24931   0.24995   0.226647  0.237694  0.237879  0.216076  0.192437
 0.25  0.250528  0.249134  0.249728  0.248744  0.273746  0.245936  0.263367  0.245737  0.211411
```

# References

> [Adaptive online portfolio strategy based on exponential gradient updates](https://doi.org/10.1007/s10878-021-00800-7)

