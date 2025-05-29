```
amount(x)
```

If is an object with an amount component (e.g. a `Cashflow`), will retrun that amount component, otherwise just `x`.

# Examples

```julia-repl
julia> FinanceCore.amount(Cashflow(1.,3.))
1.0

julia> FinanceCore.amount(1.)
1.0
```
