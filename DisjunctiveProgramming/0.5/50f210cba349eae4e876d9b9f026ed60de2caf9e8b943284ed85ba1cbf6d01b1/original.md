```
Logical{T}
```

Tag for creating logical variables using `@variable`. Most often this will  be used to enable the syntax:

```julia
@variable(model, var_expr, Logical, [kwargs...])
```

which creates a [`LogicalVariable`](@ref) that will ultimately be  reformulated into a binary variable of the form:

```julia
@variable(model, var_expr, Bin, [kwargs...])
```

To include a tag that is used to create the reformulated variables, the syntax  becomes:

```julia
@variable(model, var_expr, Logical(MyTag()), [kwargs...])
```

which creates a [`LogicalVariable`](@ref) that is associated with `MyTag()` such  that the reformulation binary variables are of the form:

```julia
@variable(model, var_expr, Bin, MyTag(), [kwargs...])
```
