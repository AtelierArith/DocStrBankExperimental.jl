```
push!(pacc::PairAccumulator, value::Number)
```

Overload `Base.push!` for a [`PairAccumulator`](@ref). One can only  `push!` a single `value <: Number` at a time into this type of accumulator.
