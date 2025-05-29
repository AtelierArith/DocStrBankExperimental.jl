```
(t::TimerOutput)(f, name=string(repr(f))) -> InstrumentedFunction
```

Instruments `f` by the [`TimerOutput`](@ref) `t` returning an `InstrumentedFunction`. This function can be used just like `f`, but whenever it is called it stores timing results in `t`.
