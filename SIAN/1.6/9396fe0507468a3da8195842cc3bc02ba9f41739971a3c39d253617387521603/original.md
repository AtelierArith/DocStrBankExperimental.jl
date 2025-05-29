```
macro ODEmodel(ex::Expr...)
```

Macro for creating an ODE from a list of equations and injecting all variables into the global scope.

Example:

```
ode = @ODEmodel(
    x1'(t) = - a * x1(t),
    y1(t) = x1(t),
)
```
