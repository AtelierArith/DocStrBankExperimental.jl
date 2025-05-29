```
@register_discontinuity f(arg1, arg2, ...) root_expr left_expr right_expr
```

Utility macro to register functions with discontinuities. The function `f` with arguments `arg1, arg2, ...` has a `rootfunction` of `root_expr`, a `left_continuous_function` of `left_expr` and `right_continuous_function` of `right_expr`. `root_expr`, `left_expr` and `right_expr` are all expressions in terms of `arg1, arg2, ...`.

For example, `max(x, y)` can be registered as `@register_discontinuity max(x, y) x - y y x`.

See also: [`rootfunction`](@ref)
