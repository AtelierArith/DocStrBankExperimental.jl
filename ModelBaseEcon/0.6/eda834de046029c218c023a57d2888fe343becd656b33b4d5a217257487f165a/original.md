```
@autoexogenize model begin
    varname = shkname
    ...
end
```

Define a mapping between variables and shocks that can be used to conveniently  swap exogenous and endogenous variables.

You can also remove pairs from the model by prefacing each removed pair with `@delete`.
