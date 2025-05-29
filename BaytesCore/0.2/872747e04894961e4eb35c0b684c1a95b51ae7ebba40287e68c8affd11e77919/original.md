```julia
struct PrintDefault
```

Default arguments for printing summary statistics after sampling.

# Fields

  * `Ndigits::Int64`: Number of Digits for rounding summary statistics.
  * `quantiles::Vector{Float64}`: Quantiles for summary statistics.
