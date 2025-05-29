```
default_value(x)
```

Return the default value of a symbolic variable `x` or `nothing` if it doesn't have any. Return `x` if `x` is not a symbolic variable. The difference with `ModelingToolkit.getdefault` is that this function will not error on the absence of a default value.
