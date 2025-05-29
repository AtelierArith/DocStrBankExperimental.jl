```
solve(eq::SymboliclEquation, x)
```

Very *simple* symbolic equations can be solved with the unexported `solve` method. This example shows a usage.

```{julia}
@symbolic w p; @symbolic h  # two variables, one parameter
import SimpleExpressions: solve, D
constraint = p ~ 2w + 2h
A = w * h

u = solve(constraint, h)
A = A(u) # use equation in replacement
v = solve(D(A, w) ~ 0, w)
```
