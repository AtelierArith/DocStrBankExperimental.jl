# lppd

Generic version of Log Pointwise Predictive Density computation, which is similar to `simulate` function, but additionally computes log density for the target values.

```julia
lppd(df, rx_to_dist, xseq, yseq)

```

## Required arguments

  * `df::DataFrame`: data frame with parameters
  * `rx_to_dist::Function`: callable with two arguments: row object and x value.

Has to return `Distribution` instance

  * `xseq`: sequence of x values to be passed to the callable
  * `yseq`: sequence of target values for log density calculation.

## Return values

Vector of float values with the same size as `xseq` and `yseq`.

## Examples

```jldoctest
julia> using StatisticalRethinking, DataFrames, Distributions

julia> df = DataFrame(:mu => [0.0, 1.0])
2×1 DataFrame
 Row │ mu
     │ Float64
─────┼─────────
   1 │     0.0
   2 │     1.0

julia> lppd(df, (r, x) -> Normal(r.mu + x, 1.0), 0:3, 3:-1:0)
4-element Vector{Float64}:
 -3.5331959794720684
 -1.1380087295845114
 -1.9106724357818656
 -6.082335295491998
```
