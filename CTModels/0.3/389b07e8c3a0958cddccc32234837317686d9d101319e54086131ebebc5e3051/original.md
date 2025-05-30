```julia
time_grid(
    sol::CTModels.Solution{<:CTModels.TimeGridModel{T<:Union{StepRangeLen, AbstractVector{<:Real}}}}
) -> Union{StepRangeLen, AbstractVector{<:Real}}

```

Return the time grid of the optimal control solution.
