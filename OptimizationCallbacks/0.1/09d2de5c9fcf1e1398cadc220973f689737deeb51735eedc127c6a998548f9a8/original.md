```
EventTrigger(events)
```

Triggers at given events using the [`trigger!`](@ref) function.

### Example

```jldoctest
julia> using OptimizationCallbacks

julia> callback = Callback(EventTrigger((:start, :end)), (_, value,_ ,_) -> @info( "Current value: " * string(value)));

julia> begin
           @info "Start."
           OptimizationCallbacks.trigger!(callback, :start)
           callback(nothing, 10.)
           callback(nothing, 9.)
           callback(nothing, 7.)
           OptimizationCallbacks.trigger!(callback, :end)
           callback(nothing, 6.)
       end;
[ Info: Start.
[ Info: Current value: 10.0
[ Info: Current value: 6.0
```
