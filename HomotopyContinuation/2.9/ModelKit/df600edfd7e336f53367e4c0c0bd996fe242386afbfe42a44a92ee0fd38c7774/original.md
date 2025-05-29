```
nvariables(expr::Expression; parameters = Variable[])
nvariables(exprs::AbstractVector{Expression}; parameters = Variable[])
```

Obtain the number of variables used in the given expression not counting the the ones declared in `parameters`.
