```julia
function statistic(x::IntVec, y::UniData, stat::StudentT_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...)
```

Student's *t* statistic for independent samples, see [Edgington (1995)](@ref "References"), p. 3.

For all arguments except `stat` and examples see the [`statistic`](@ref) method for `AnovaF_IS` here above.
