```
plot(f::Function, lower::Number, upper::Number, elements::ElementOrFunction...;
     mapping...)
```

Plot the function or expression `f`, which takes a single argument or operates on a single variable, respectively, between the `lower` and `upper` bounds.  See [`Stat.func`](@ref) and [`Geom.line`](@ref).
