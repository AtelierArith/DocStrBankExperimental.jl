```
AbstractTimeDependentOperator{BL,BR} <: AbstractOperator{BL,BR}
```

Abstract type providing a time-dependent operator interface. Time-dependent operators have internal "clocks" that can be addressed with [`set_time!`](@ref) and [`current_time`](@ref). A shorthand `op(t)`, equivalent to `set_time!(copy(op), t)`, is available for brevity.

A time-dependent operator is always concrete-valued according to the current time of its internal clock.
