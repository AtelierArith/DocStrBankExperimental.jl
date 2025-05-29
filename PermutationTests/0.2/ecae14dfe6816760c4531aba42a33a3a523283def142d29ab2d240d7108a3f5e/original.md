```julia
function statistic(x::IntVec, y::UniData, stat::SumGroupTotalsSqN_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...)
```

Sum of squared group totals divided each by the group numerosity. 

Equivalent to the 1-way ANOVA for independent samples *F* test statistic in general, see [Statistic](@ref).

For optional keyword arguments `k` and `ns` and for examples,  see the [`statistic`](@ref) method for `AnovaF_IS` here above.
