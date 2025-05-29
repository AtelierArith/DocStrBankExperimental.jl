```
set_time!(o::AbstractOperator, t::Number)
```

Sets the clock of an operator (see [`AbstractTimeDependentOperator`](@ref)). If `o` contains other operators (e.g. in case `o` is a `LazyOperator`), recursively calls `set_time!` on those.

This does nothing in case `o` is not time-dependent.
