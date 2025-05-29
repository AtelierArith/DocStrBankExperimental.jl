```
unroll(
    moving_average::Vector{Float64},
    window::Int64;
    initial_conditions::U=nothing,
    assert_natural::Bool=false,
) where {U<:Union{Tuple{Vararg{Union{Int64,Float64}}},Nothing}}
```

Retrieve original time series (i.e. unroll) from its moving average `moving_average`. 

# Arguments

  * `moving_average::Vector{Float64}`: the time series representing the moving average to unroll;
  * `window:::Int64`: the width of the moving average;
  * `initial_conditions::U = nothing`: the initial values of the original time series to be recovered. It may be a `Tuple` of `window-1` float or integer values, or `nothing` if initial conditions are unknown;
  * `assert_natural::Bool = false` default boolean argument. If true, then the pipeline will try to recover a time series of natural numbers only. More then one acceptable time series (where "acceptable" means that it reproduces `moving_average`) may be found and returned.

NB: If `isnothing(initial_conditions) && !assert_natural` , then only an approximate method may be used, see this [StackExchange post](https://stats.stackexchange.com/a/68002).
