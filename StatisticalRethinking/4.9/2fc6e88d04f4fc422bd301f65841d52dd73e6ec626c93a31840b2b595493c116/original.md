# simulate

Generic simulate of predictions using callable returning distribution to sample from.

```julia
simulate(df, rx_to_dist, xrange; return_dist, seed)

```

## Required arguments

  * `df::DataFrame`: data frame with parameters in each row
  * `rx_to_dist::Function`: callable with two arguments: row object and x value. Have to return `Distribution` instance.
  * `xrange`: iterable with arguments

## Optional arguments

  * `return_dist::Bool = false`: if set to `true`, distributions will be returned, not their samples
  * `seed::Int = missing`: sets the random seed

## Return value

Vector were each item is generated from every item in xrange argument. Each item is again a vector obtained from `rx_to_dist` call to obtain a distribution and then sample from it. If argument `return_dist=true`, sampling step will be omitted.

## Examples

```jldoctest
julia> using StatisticalRethinking, DataFrames, Distributions

julia> d = DataFrame(:mu => [1.0, 2.0], :sigma => [0.1, 0.2])
2×2 DataFrame
 Row │ mu       sigma
     │ Float64  Float64
─────┼──────────────────
   1 │     1.0      0.0
   2 │     2.0      0.0

julia> simulate(d, (r,x) -> Normal(r.mu+x, r.sigma), 0:1)
2-element Vector{Vector{Float64}}:
 [1.0, 2.0]
 [2.0, 3.0]

julia> simulate(d, (r,x) -> Normal(r.mu+x, r.sigma), 0:1, return_dist=true)
2-element Vector{Vector{Normal{Float64}}}:
 [Normal{Float64}(μ=1.0, σ=0.0), Normal{Float64}(μ=2.0, σ=0.0)]
 [Normal{Float64}(μ=2.0, σ=0.0), Normal{Float64}(μ=3.0, σ=0.0)]

```
