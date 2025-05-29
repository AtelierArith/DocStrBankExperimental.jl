```
timeInState()
timeInState(state)
```

Get the time (in seconds) spent in a state in a finite state machine.

When used to query the time spent in the enclosing state, the method without arguments is used, i.e.,

```julia
@mtkmodel FSM begin
    ...
    @equations begin
        var(k+1) ~ timeInState() >= 2 ? 0.0 : var(k)
    end
end
```

If used to query the residence time of another state, the state is passed as an argument.

This operator can be used in both equations and transition conditions.

See also [`ticksInState`](@ref) and [`entry`](@ref)
