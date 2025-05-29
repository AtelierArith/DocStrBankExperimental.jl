```
Rate(rate[,frequency=1])
Rate(rate,frequency::Frequency)
```

Rate is a type that encapsulates an interest `rate` along with its compounding `frequency`.

Periodic rates can be constructed via `Rate(rate,frequency)` or `Rate(rate,Periodic(frequency))`. If not given a second argument, `Rate(rate)` is equivalent to `Rate(rate,Periodic(1))`.

Continuous rates can be constructed via `Rate(rate, Inf)` or `Rate(rate,Continuous())`.

# Examples

```julia-repl
julia> Rate(0.01,Continuous())
Rate(0.01, Continuous())

julia> Continuous(0.01)
Rate(0.01, Continuous())

julia> Continuous()(0.01)
Rate(0.01, Continuous())

julia> Rate(0.01,Periodic(2))
Rate(0.01, Periodic(2))

julia> Periodic(0.01,2)
Rate(0.01, Periodic(2))

julia> Periodic(2)(0.01)
Rate(0.01, Periodic(2))

julia> Rate(0.01)
Rate(0.01, Periodic(1))

julia> Rate(0.01,2)
Rate(0.01, Periodic(2))

julia> Rate(0.01,Periodic(4))
Rate(0.01, Periodic(4))

julia> Rate(0.01,Inf)
Rate(0.01, Continuous())

```
