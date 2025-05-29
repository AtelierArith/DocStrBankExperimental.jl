```
DSProblem{T, UT}(N::Int; poll::AbstractPoll=LTMADS{T}(),
                         search::AbstractSearch=NullSearch(),
                         objective::Union{Function,Nothing}=nothing,
                         initial_point::Vector=zeros(T, N),
                         iteration_limit::Int=1000,
                         function_evaluation_limit::Int=5000,
                         sense::ProblemSense=Min,
                         full_output::Bool=false,
                         granularity::Vector=zeros(T, N),
                         min_mesh_size::Union{T,Nothing}=nothing,
                         min_poll_size::Union{T,Nothing}=nothing,
                         kwargs...
                         ) where T
```

Return a problem definition for an `N` dimensional problem using numbers of type `T`.

`poll` and `search` specify the poll and search step algorithms to use. The default choices are [`LTMADS`](@ref) and [`NullSearch`](@ref) respectively.

The problem can contain user-defined parameters that are passed into every objective function evaluation. These parameters will be stored inside a field of type `UT`.
