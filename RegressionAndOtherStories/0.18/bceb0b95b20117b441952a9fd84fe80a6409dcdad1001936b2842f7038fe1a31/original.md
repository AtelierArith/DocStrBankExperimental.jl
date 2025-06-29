# PI

Compute percentile central interval of data. Returns vector of bounds.

```julia
PI(data; perc_prob)

```

## Required arguments

  * `data`: iterable over data values

## Optional arguments

  * `perc_prob::Float64=0.89`: percentile interval to calculate

## Examples

```jldoctest
julia> using StatisticalRethinking

julia> PI(1:10)
2-element Vector{Float64}:
 1.495
 9.505

julia> PI(1:10; perc_prob=0.1)
2-element Vector{Float64}:
 5.05
 5.95

```
