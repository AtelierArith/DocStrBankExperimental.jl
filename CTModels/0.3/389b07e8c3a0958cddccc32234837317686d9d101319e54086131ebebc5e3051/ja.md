```julia
time_grid(
    sol::CTModels.Solution{<:CTModels.TimeGridModel{T<:Union{StepRangeLen, AbstractVector{<:Real}}}}
) -> Union{StepRangeLen, AbstractVector{<:Real}}

```

最適制御解の時間グリッドを返します。
