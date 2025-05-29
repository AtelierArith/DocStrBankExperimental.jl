```julia
function statistic(x::UniData, y::UniData, stat::Sum; 
                kwargs...)  
```

Sum of the elements in input data vector `y`.

Equivalent to the one-sample *t* test statistic in general, see [Statistic](@ref).

`x` is the [`membership(::OneSampStatistic)`](@ref) vector.
