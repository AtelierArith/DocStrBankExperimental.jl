```
struct ProblemState
function ProblemState(; u = nothing, p = nothing, t = nothing, h = nothing)
```

A value provider struct which can be used as an argument to the function returned by [`getsym`](@ref) or [`setsym`](@ref). It stores the state vector, parameter object and current time, and forwards calls to [`state_values`](@ref), [`parameter_values`](@ref), [`current_time`](@ref), [`set_state!`](@ref), [`set_parameter!`](@ref) to the contained objects.

A history function may be provided using the `h` keyword, which will be returned with [`get_history_function`](@ref).
