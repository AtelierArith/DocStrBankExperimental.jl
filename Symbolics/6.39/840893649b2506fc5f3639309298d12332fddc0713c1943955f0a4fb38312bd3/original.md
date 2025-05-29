```
ticksInState()
ticksInState(state)
```

Get the number of ticks spent in a state in a finite state machine.

When used to query the number of ticks spent in the enclosing state, the method without arguments is used, i.e.,

```julia
@mtkmodel FSM begin
    ...
    @equations begin
        var(k+1) ~ ticksInState() >= 2 ? 0.0 : var(k)
    end
end
```

If used to query the number of ticks in another state, the state is passed as an argument.

This operator can be used in both equations and transition conditions.

See also [`timeInState`](@ref) and [`entry`](@ref)
