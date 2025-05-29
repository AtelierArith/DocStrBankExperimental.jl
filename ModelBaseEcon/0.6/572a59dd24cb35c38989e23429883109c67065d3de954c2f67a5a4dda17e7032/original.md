```
peval(params, what)
```

Evaluate the given expression in the context of the given parameters `params`.

If `what` is a `ModelParam`, its current value is returned. If it's a link and  there's a chance it might be out of date, call [`update_links!`](@ref).

If `what` is a Symbol or an Expr, all mentions of parameter names are substituted by their values and the expression is evaluated.

If `what is any other value, it is returned unchanged.`

See also: [`Parameters`](@ref), [`@alias`](@ref), [`@link`](@ref), [`ModelParam`](@ref), [`update_links!`](@ref).
