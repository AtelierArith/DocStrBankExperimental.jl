```
timepoint(x,t)
```

If `x` is an object with a defined time component (e.g. a `Cashflow`), will return that time component, otherwise will return `t`. This is useful in handling situations where you want to handle either `Cashflow`s or separate amount and time vectors.

# Example

```julia-repl
julia> FinanceCore.timepoint(Cashflow(1.,3.),"ignored")
3.0

julia> FinanceCore.timepoint(1.,4.)
4.0
```
