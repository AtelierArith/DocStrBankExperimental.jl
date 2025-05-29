```
@NLexpression(args...)
```

Efficiently build a nonlinear expression which can then be inserted in other nonlinear constraints and the objective. See also [`@expression`]. For example:

```julia
@NLexpression(model, my_expr, sin(x)^2 + cos(x^2))
@NLconstraint(model, my_expr + y >= 5)
@NLobjective(model, Min, my_expr)
```

Indexing over sets and anonymous expressions are also supported:

```julia
@NLexpression(m, my_expr_1[i=1:3], sin(i * x))
my_expr_2 = @NLexpression(m, log(1 + sum(exp(x[i])) for i in 1:2))
```
