```
@infiltry expr
```

Wraps expression in a try block, infiltrate if an exception is raised. Equivalent to:

```julia
try
    expr
catch
    @infiltrate
    rethrow()
end
```

If `expr` is of the form `x = f(...)`, we take `x` out of the scope

```julia
x = try
    f(...)
catch
    @infiltrate
    rethrow()
end
```
