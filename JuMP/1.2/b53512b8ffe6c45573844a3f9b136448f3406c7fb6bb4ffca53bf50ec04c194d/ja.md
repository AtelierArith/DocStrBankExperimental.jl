```
@NLexpression(args...)
```

非線形式を効率的に構築し、他の非線形制約や目的に挿入できるようにします。 [`@expression`] も参照してください。例えば：

```julia
@NLexpression(model, my_expr, sin(x)^2 + cos(x^2))
@NLconstraint(model, my_expr + y >= 5)
@NLobjective(model, Min, my_expr)
```

集合に対するインデクシングや匿名式もサポートされています：

```julia
@NLexpression(m, my_expr_1[i=1:3], sin(i * x))
my_expr_2 = @NLexpression(m, log(1 + sum(exp(x[i])) for i in 1:2))
```
