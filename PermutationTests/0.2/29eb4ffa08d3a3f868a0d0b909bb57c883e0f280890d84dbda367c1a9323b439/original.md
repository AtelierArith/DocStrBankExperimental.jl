```julia
function statistic(x::IntVec, y::UniData, stat::SumTreatTotalsSq_RM; 
                ns::@NamedTuple{n::Int, k::Int}, 
                kwargs...)
```

Sum of squared treatment totals.

Equivalent to the 1-way ANOVA for repeated measures *F* test statistic in general, see [Statistic](@ref).

For optional keyword argument `ns` see the [`statistic`](@ref) method for `AnovaF_RM` here above.
