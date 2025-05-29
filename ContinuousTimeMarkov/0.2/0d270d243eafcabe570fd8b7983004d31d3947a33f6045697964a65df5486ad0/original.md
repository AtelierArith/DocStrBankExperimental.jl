```julia
CompetingPoisson(rates; events)

```

The first arrival from competing Poisson point processes with the given `rates`.

`rand` returns a `NamedTuple{(:duration,:event)}`, where `duration` is the duration until the first event and `event` is drawn from `events`.

Varios properties are supported, see [`propertynames`](@ref).

# Note

The distribution of `duration` is `Exponential(1/sum(rates))`, so this process can also be thought of as competing exponentials.
