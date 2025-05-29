```
@expression(args...)
```

Efficiently builds a linear or quadratic expression but does not add to model immediately. Instead, returns the expression which can then be inserted in other constraints. For example:

```julia
@expression(m, shared, sum(i*x[i] for i=1:5))
@constraint(m, shared + y >= 5)
@constraint(m, shared + z <= 10)
```

The `ref` accepts index sets in the same way as `@variable`, and those indices can be used in the construction of the expressions:

```julia
@expression(m, expr[i=1:3], i*sum(x[j] for j=1:3))
```

Anonymous syntax is also supported:

```julia
expr = @expression(m, [i=1:3], i*sum(x[j] for j=1:3))
```
