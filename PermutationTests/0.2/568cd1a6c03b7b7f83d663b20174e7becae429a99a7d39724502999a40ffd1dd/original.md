```julia
function statistic(x::IntVec, y::UniData, stat::Group1Total_IS; 
                kwargs...)            
```

Sum of observations for group 1.

Equivalent to the Students's *t* test statistic for independent samples for diretional tests, see [Statistic](@ref).

For arguments `x` and `y` and for examples, see the [`statistic`](@ref) method for `AnovaF_IS` here above.
