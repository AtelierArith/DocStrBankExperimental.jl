```
accumulation(rate, t)
accumulation(rate, from, to)
```

Accumulate `rate` for a time `t` or for an interval `(from, to)`. If `rate` is not a `Rate`, it will be assumed to be a `Periodic` rate compounded once per period, i.e. `Periodic(rate,1)`. 

```
# Examples
```

```julia-repl
julia> accumulation(0.03, 10)
1.3439163793441222

julia> accumulation(Periodic(0.03, 2), 10)
1.3468550065500535

julia> accumulation(Continuous(0.03), 10)
1.3498588075760032

julia> accumulation(0.03, 5, 10)
1.1592740743
```
