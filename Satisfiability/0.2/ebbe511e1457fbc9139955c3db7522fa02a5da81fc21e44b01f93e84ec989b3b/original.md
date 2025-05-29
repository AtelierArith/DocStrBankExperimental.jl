```
value(z::BoolExpr)
value(z::Array{BoolExpr})
```

Returns the satisfying assignment of `z`, or `nothing` if no satisfying assignment is known. In the array-valued case, returns `Array{Bool}` or `Array{nothing}`.

It's possible to return an array of mixed `Bool` and `nothing`. This could occur if some variables in an array do not appear in a problem, because `sat!(problem)` will not set the values of variables that do not appear in `problem`.
