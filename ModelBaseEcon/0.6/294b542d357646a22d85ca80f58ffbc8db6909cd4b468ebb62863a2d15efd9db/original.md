```
@variables model name1 name2 ...
@variables model begin
    name1
    name2
    ...
end
```

Declare the names of variables in the model.

In the `begin-end` version the variable names can be preceeded by a description (like a docstring) and flags like `@log`, `@steady`, `@exog`, etc. See [`ModelVariable`](@ref) for details about this.

You can also remove variables from the model by prefacing one or more  variables with `@delete`.
