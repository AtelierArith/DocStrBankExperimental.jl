```julia
function statistic(x::IntVec, y::UniData, stat::SumGroupTotalsSq_IS; 
                k::Into=nothing, 
                kwargs...)
```

Sum of squared group totals. 

Equivalent to the 1-way ANOVA for independent samples *F* test statistic in balanced designs, see [Statistic](@ref). 

For optional keyword argument `k`, see the [`statistic`](@ref) method for `AnovaF_IS` here above.
